<template>
  <div :class="['spinner', spinnerSize, spinnerVariant]"></div>
</template>

<script>
export default {
  props: {
    size: {
      default: "medium",
      type: String,
      validator(value) {
        return ["small", "medium", "large"].includes(value);
      },
    },
    variant: {
      default: "dark",
      type: String,
      validator(value) {
        return ["light", "dark"].includes(value);
      },
    },
  },

  computed: {
    spinnerSize() {
      const sizes = {
        small: "h-[22px] w-[22px]",
        medium: "h-[36px] w-[36px]",
        large: "h-[52px] w-[52px]",
      }
      return sizes[this.size]
    },
    spinnerVariant() {
      const variants = {
        dark: "border-[4px] border-solid border-[#2f2f2f] border-l-[#5f8bee]",
        light: "border-[4px] border-solid border-gray-500 border-l-white",
      }
      return variants[this.variant];
    }
  }
};
</script>

<style scoped>
.spinner {
  margin: auto;
  border-radius: 50%;
  animation: spin 1s ease infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}
</style>
