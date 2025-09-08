<template>
  <button :class="['icon-btn', btnColor]">
    <slot />
  </button>
</template>

<script>
export default {
  props: {
    variant: {
      type: String,
      default: "danger",
      validator(value) {
        return ["danger", "warning", "info", "succes"].includes(value);
      },
    },
  },

  computed: {
    btnColor() {
      const colors = {
        danger: "text-danger-500",
        warning: "text-warning-500",
        info: "text-gradient-500",
        succes: "text-accent-500",
      };
      return colors[this.variant];
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
