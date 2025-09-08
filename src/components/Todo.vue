<template>
  <li class="todo" v-bind:key="id">
    <p>{{ title }}</p>
    <div class="flex gap-4">
      <IconBtn @click.prevent="$emit('edit-todo', index)" variant="info" size="small">
        <i class="bi bi-pencil-square"></i>
      </IconBtn>
      <IconBtn @click.prevent="$emit('remove-todo', index)" variant="danger" size="small">
        <i class="bi bi-trash"></i>
      </IconBtn>
    </div>
  </li>
</template>

<script>

import IconBtn from './buttons/IconBtn.vue';

export default {

  components: { IconBtn },

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

  emits: ['remove-todo', 'edit-todo']
}
</script>

<style>
@reference "../assets/style.css";

.todo {
  @apply py-4 px-6 flex justify-between items-center bg-primary-400 rounded-md
}
</style>
