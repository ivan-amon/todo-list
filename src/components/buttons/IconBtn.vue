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
        return ["danger", "warning", "info", "succes"].includes(value);
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
        succes: "text-accent-500",
      };
      return colors[this.type];
    },
  },
};
</script>

<style scoped>
@reference "../../assets/style.css";

.icon-btn {
  @apply rounded-md text-xl outline-none cursor-pointer;
}
.icon-btn:hover, .icon-btn:focus {
  @apply scale-120
}
</style>
