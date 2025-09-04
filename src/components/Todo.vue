<template>
  <li class="todo" v-bind:key="id">
    <p>{{ title }}</p>
    <div>
      <button @click.prevent="$emit('remove-todo', index)" class="btn-danger">
        <i class="bi bi-trash"></i>
      </button>
    </div>
  </li>
</template>

<script>
export default {

  props: {
    id: {
      type: Number,
      required: true
    },
    index: {
      type: Number,
      required: true
    },
    title: {
      type: String,
      required: true
    },
  },

  emits: ['remove-todo']
}
</script>
