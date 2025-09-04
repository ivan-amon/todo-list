<template>
  <ul class="gap-5 flex flex-col">
    <Todo
      v-for="(todo, index) in todos"
      :id="todo.id"
      :index="index"
      :title="todo.title"
      @remove-todo="removeTodo"
    />
  </ul>
</template>

<script>
import Todo from './Todo.vue';

export default {
  
}
</script>