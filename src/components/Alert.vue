<template>
  <div v-if="show" class="py-2">
    <div :class="['alert', alertColor]">
      <p>{{ message }}</p>
      <button @click="$emit('close')" class="hover:scale-120 pt-0.5">
        <i class="bi bi-x text-3xl"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {

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

