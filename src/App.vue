<template>
  <Navbar />
  <main class="px-2 pt-5 md:pt-10 md:px-8 lg:px-20 xl:px-32 2xl:px-60">
    <section class="px-6">
      <Alert
        :show="alert.show"
        :message="alert.message"
        :type="alert.type"
        @close="alert.show = false"
      />
    </section>

    <Modal v-if="editTodoForm.show" @close="editTodoForm.show = false">
      <template #header>
        <h2 class="text-4xl text-gradient font-semibold inline-block">
          Edit to-do
        </h2>
      </template>
      <template #body>
        <label for="todo" class="text-xl">Title</label>
        <div class="border-gradient w-[100%] md:w-[70%] xl:w-[75%]">
          <input
            type="text"
            class="todo-input"
            v-model="editTodoForm.todo.title"
          />
        </div>
      </template>
      <template #footer>
        <Btn @click.prevent="updateTodo" variant="submit"> Submit </Btn>
        <Btn @click.prevent="editTodoForm.show = false" variant="danger">
          Close
        </Btn>
      </template>
    </Modal>

    <section class="px-6 pt-3 mb-12 mt-3 md:mt-4">
      <AddTodoForm @submitTodo="addTodo" :isLoading="isPostingTodo" />
    </section>

    <section class="px-6 pb-3">
      <Spinner v-if="isLoading" size="large" variant="dark"/>
      <ul v-else class="gap-5 flex flex-col">
        <Todo
          v-for="(todo, index) in todos"
          :id="todo.id"
          :index="index"
          :title="todo.title"
          @remove-todo="removeTodo"
          @edit-todo="showEditTodoForm"
        />
      </ul>
    </section>
  </main>
</template>

<script>
import AddTodoForm from "./components/AddTodoForm.vue";
import Alert from "./components/Alert.vue";
import Btn from "./components/buttons/Btn.vue";
import Modal from "./components/Modal.vue";
import Navbar from "./components/Navbar.vue";
import Spinner from "./components/Spinner.vue";
import Todo from "./components/Todo.vue";
import axios from "axios";

export default {
  components: { Alert, Navbar, AddTodoForm, Todo, Modal, Btn, Spinner },

  data() {
    return {
      todoTitle: "",
      todos: [],
      alert: {
        show: false,
        message: "",
        type: "danger"
      },
      isLoading: false,
      isPostingTodo: false,
      editTodoForm: {
        show: false,
        todo: {
          id: 0,
          title: "",
        },
      },
    };
  },

  created() {
    this.fetchTodos();
  },

  methods: {
    async fetchTodos() {
      this.isLoading = true;
      try {
        const res = await axios.get("http://localhost:4600/todos");
        this.todos = await res.data;
      } catch(e) {
        this.showAlert("Failed loading to-dos");
      }
      this.isLoading = false;
    },

    showAlert(message, type = "danger") {
      this.alert.show = true,
      this.alert.message = message;
      this.alert.type = type;
    },

    async addTodo(title) {
      if (title.trim() === "" || !title) {
        this.showAlert("To-do title is required!", "danger")
        return;
      }

      this.isPostingTodo = true;
      const res = await axios.post("http://localhost:4600/todos", {
        title,
      });

      this.isPostingTodo = false;
      this.todos = this.todos.concat([res.data]);
      this.alert.show = false;
    },

    showEditTodoForm(index) {
      this.editTodoForm.show = true;
      this.editTodoForm.todo = { ...this.todos[index] };
    },

    updateTodo() {
      const todo = this.todos.find(
        (todo) => todo.id === this.editTodoForm.todo.id
      );
      todo.title = this.editTodoForm.todo.title;
      this.editTodoForm.show = false;
    },

    async removeTodo(id) {
      await axios.delete(`http://localhost:4600/todos/${id}`);
      this.fetchTodos();
    },
  },
};
</script>
