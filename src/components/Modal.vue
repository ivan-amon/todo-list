<template>
  <div v-if="show" class="modal">
    <div class="modal-content">

      <div class="modal-header">
        <slot name="header"/>
      </div>

      <div class="modal-body flex flex-col px-6
                  md:flex-row md:justify-center md:items-center">
        <slot name="body"/>
      </div>

      <div class="modal-footer">
        <slot name="footer"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    show: {
      default: false,
      type: Boolean,
    },
  },
};
</script>

<style scoped>
@reference "../assets/style.css";

.modal {
  @apply fixed z-[1] pt-40 left-0 top-0 w-full h-full overflow-auto bg-black/75;
}


.modal-content {
  @apply relative mx-auto p-0  w-4/5;
  @apply shadow-[0_4px_8px_rgba(0,0,0,0.2),0_6px_20px_rgba(0,0,0,0.19)];
  @apply animate-[animatetop_0.4s];
}

@-webkit-keyframes animatetop {
  from {top:-300px; opacity:0} 
  to {top:0; opacity:1}
}

@keyframes animatetop {
  from {top:-300px; opacity:0}
  to {top:0; opacity:1}
}

.modal-header {
  @apply py-4 px-4 md:px-10 bg-primary-600 text-white rounded-t-lg;
}

.modal-body {
  @apply pb-8 pt-8 md:pt-16 bg-primary-400 px-6 md:px-4 gap-4 md:gap-10;
}

.modal-footer {
  @apply flex justify-center align-middle gap-10 pb-16 pt-4 px-4 bg-primary-400 rounded-b-lg;
}
</style>
