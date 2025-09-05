<template>
  <button @click.prevent="$emit('click')" :class="['btn', btnType]">
    <slot/>
  </button>
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: 'submit',
      validator(value) {
        return ['submit', 'danger'].includes(value)
      }
    }
  },
  
  computed: {
    btnType() {
      const backgrounds = {
        submit: `bg-gradient-to-r from-[var(--color-accent-500)] to-[var(--color-gradient-500)]
                 hover:from-[var(--color-accent-400)] hover:to-[var(--color-gradient-400)]`,
        danger: `bg-gradient-to-r from-[var(--color-danger-500)] to-[var(--color-warning-500)]
                 hover:from-[var(--color-danger-600)] hover:to-[var(--color-warning-600)]`
      }
      return backgrounds[this.type]
    }
  },

  emits: ['click']
}
</script>

<style scoped>
@reference "../../assets/style.css";

.btn {
  @apply rounded-md cursor-pointer md:mt-0 py-3 px-8 2xl:px-12;
}
</style>