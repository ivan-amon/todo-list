<template>
  <form
    class="mt-2 mb-12 flex flex-col justify-center items-end md:flex-row md:justify-between md:items-center"
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
    <div>
      <button
        @click.prevent="$emit('submit-todo', todoTitle)"
        class="btn mt-6 md:mt-0 py-3 px-8 2xl:px-12"
        type="submit"
      >
        Add Todo
      </button>
    </div>
  </form>
</template>

<script>
export default {
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
