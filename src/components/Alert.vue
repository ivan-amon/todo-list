<template>
  <div v-if="show" class="md:mt-4">
    <div :class="['alert', alertColor]">
      <p>{{ message }}</p>
      <IconBtn @click="$emit('close')" type="danger" size="small">
        <i class="bi bi-x-circle-fill"></i>
      </IconBtn>
    </div>
  </div>
</template>

<script>

import IconBtn from './buttons/IconBtn.vue';

export default {

  components: { IconBtn },

  props: {
    message: {
      required: true,
      type: String
    },
    show: {
      required: true,
      type: Boolean
    },
    type: {
      type: String,
      default: 'danger',
      validator(value) {
        return ['danger', 'warning', 'info'].includes(value)
      }
    }
  },

  computed: {
    alertColor() {
      const colors = {
        danger: 'border-danger-500  text-danger-500 border-2',
        warning: 'border-warning-500  text-warning-500 border-2',
        info: 'border-gradient-500  text-gradient-500 border-2'
      }
      return colors[this.type] ?? colors['danger']
    }
  },

  emits: ['close'],
}
</script>

<style>
@reference "../assets/style.css";

.alert {
  @apply flex justify-between items-center;
  @apply cursor-default py-2 px-6 rounded-md bg-primary-400;
}
</style>

