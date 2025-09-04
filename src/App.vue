<template>
  <Navbar />
  <main class="px-2 pt-5 md:pt-10 md:px-8 lg:px-20 xl:px-32 2xl:px-60">
    <section class="px-6 py-3 mt-3">
      <Alert
        :show="showAlert"
        message="Todo title is required!"
        type="danger"
        @close="showAlert = false"
      />
      <AddTodoForm @submitTodo="addTodo" />
      <ul class="gap-5 flex flex-col">
        <Todo
          v-for="(todo, index) in todos"
          :id="todo.id"
          :index="index"
          :title="todo.title"
          @remove-todo="removeTodo"
        />
      </ul>
    </section>
  </main>
</template>

<script>

import AddTodoForm from "./components/AddTodoForm.vue";
import Alert from "./components/Alert.vue";
import Navbar from "./components/Navbar.vue";
import Todo from "./components/Todo.vue";

export default {
  components: { Alert, Navbar, AddTodoForm, Todo },

  data() {
    return {
      todoTitle: "",
      todos: [],
      showAlert: false,
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
