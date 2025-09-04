<template>
  <nav class="mb-1 p-2 md:p-5 l:mb-5 2xl:py-7 2xl:px-6">

    <div class="flex flex-row items-center gap-4">
      <a href="#" class="logo flex items-center gap-2 md:gap-3 p-2">
        <img src="./assets/logo.svg" class="w-8 md:w-10 xl:w-12" />
        <span class="text-gradient font-semibold text-2xl md:text-4xl self-center">Todo List</span>
      </a>
      <a href="#" class="hidden md:block p-2 text-magic text-lg">Home</a>
      <a href="#" class="hidden md:block p-2 text-magic text-lg">About</a>
      <a href="#" class="hidden md:block p-2 text-magic text-lg">Logout</a>
    </div>

    <div class="flex align-middle gap-1">
      <p class="p-2 text-user cursor-default text-md md:text-lg">test@gmail.com</p>

    </div>

  </nav>

  <main class="px-2 pt-5 md:pt-10 md:px-8 lg:px-20 xl:px-32 2xl:px-60">

    <section class="px-6 py-3 mt-3">
      <Alert :show="showAlert" message="Todo title is required!" type="warning" @close="showAlert = false"/>
      <form class="mt-2 mb-12 flex flex-col justify-center items-end md:flex-row md:justify-between md:items-center">
        <div class="border-gradient w-[100%]  md:w-[70%] xl:w-[75%]">
          <input v-model="todoTitle" class="todo-input" type="text" name="todo" id="todo" />
        </div>
        <div>
          <button @click.prevent="addTodo" class="btn mt-6 md:mt-0 py-3 px-8 2xl:px-12">Add Todo</button>
        </div>
      </form>
      <ul class="gap-5 flex flex-col">
        <li v-for="(todo, index) in todos" class="todo" v-bind:key="todo.id">
          <p>{{ todo.title }}</p>
          <div>
            <button @click.prevent="removeTodo(index)" class="btn-danger">
              <i class="bi bi-trash"></i>
            </button>
          </div>
        </li>
      </ul>

    </section>
  </main>
</template>

<script>

import Alert from './components/Alert.vue';

export default {

  components: {
    Alert
  },

  data() {
    return {
      todoTitle: '',
      todos: [],
      showAlert: false
    }
  },
  methods: {

    addTodo() {

      if (this.todoTitle.trim() === '' || !this.todoTitle) {
        this.showAlert = true;
        return
      }

      this.todos = this.todos.concat([{
        id: Math.floor(Math.random() * 1000),
        title: this.todoTitle
      }])

      this.showAlert = false;
    },

    removeTodo(todoIndex) {
      this.todos = this.todos.filter((todo, id) => id !== todoIndex)
    }
  }
}
</script>