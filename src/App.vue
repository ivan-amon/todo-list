<template>
  <Navbar />
  <main class="px-2 pt-5 md:pt-10 md:px-8 lg:px-20 xl:px-32 2xl:px-60">
    
    <section class="px-6">
      <Alert
        :show="showAlert"
        message="To-do title is required!"
        type="danger"
        @close="showAlert = false"
      />
    </section>

    <Modal :show="showEditTodoModal">
      <template v-slot:header>
        <h2 class="text-4xl text-gradient font-semibold inline-block">Edit to-do</h2>
      </template>
      <template v-slot:body>
        <label for="todo" class="text-xl">Title</label>
        <div class="border-gradient w-[100%] md:w-[70%] xl:w-[75%]">
          <input type="text" class="todo-input">
        </div>
      </template>
      <template v-slot:footer>
        <Btn type="submit">
          Submit
        </Btn>
        <Btn @click="showEditTodoModal = false" type="danger">
          Close
        </Btn>
      </template>
    </Modal>

    <section class="px-6 pt-3 mb-12 mt-3 md:mt-4">
      <AddTodoForm @submitTodo="addTodo" />
    </section>

    <section class="px-6 pb-3">
      <ul class="gap-5 flex flex-col">
        <Todo
          v-for="(todo, index) in todos"
          :id="todo.id"
          :index="index"
          :title="todo.title"
          @remove-todo="removeTodo"
          @edit-todo="showEditTodoModal = true"
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
import Todo from "./components/Todo.vue";

export default {
  components: { Alert, Navbar, AddTodoForm, Todo, Modal, Btn },

  data() {
    return {
      todoTitle: "",
      todos: [],
      showAlert: false,
      showEditTodoModal: false
    };
  },

  methods: {
    addTodo(title) {
      if (title.trim() === "" || !title) {
        this.showAlert = true;
        return;
      }

      this.todos = this.todos.concat([
        {
          id: Math.floor(Math.random() * 1000),
          title,
        },
      ]);

      this.showAlert = false;
    },

    removeTodo(todoIndex) {
      this.todos = this.todos.filter((todo, id) => id !== todoIndex);
    },
  },
};
</script>
