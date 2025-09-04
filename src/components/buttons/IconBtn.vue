<template>
  <button @click.prevent="$emit('click')" :class="['icon-btn', btnColor]">
    <slot />
  </button>
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: "danger",
      validator(value) {
        return ["danger", "warning", "info"].includes(value);
      },
    },
  },

  emits: ["click"],

  computed: {
    btnColor() {
      const colors = {
        danger: "text-danger-500",
        warning: "text-warning-500",
        info: "text-gradient-500",
      };
      return colors[this.type];
    },
  },
};
</script>
