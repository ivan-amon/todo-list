<template>
  <form
    class="flex flex-col justify-center items-end md:flex-row md:justify-between md:items-center"
  >
    <div class="border-gradient w-[100%] md:w-[70%] xl:w-[75%]">
      <input
        v-model="todoTitle"
        class="todo-input"
        type="text"
        name="todo"
        id="todo"
      />
    </div>
    <div class="mt-6 md:mt-0">
      <Btn
        @click="$emit('submit-todo', todoTitle)"
        type="submit"
      >
      Add to-do
      </Btn>
    </div>
  </form>
</template>

<script>

import Btn from './buttons/Btn.vue';

export default {

  components: { Btn },

  data() {
    return {
      todoTitle: "",
    };
  },

  methods: {
    addTodo() {},
  },

  emits: ['submit-todo']
};
</script>
