<template>
  <li class="todo" v-bind:key="id">
    <p>{{ title }}</p>
    <div class="flex gap-4">
      <IconBtn @click="$emit('edit-todo', index)" type="info" size="small">
        <i class="bi bi-pencil-square"></i>
      </IconBtn>
      <IconBtn @click="$emit('remove-todo', index)" type="danger" size="small">
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

  emits: ['remove-todo']
}
</script>
