<template>
  <nav class="mb-1 p-2 md:p-5 l:mb-5 2xl:py-7 2xl:px-6">
    <div class="flex flex-row items-center gap-4">
      <a href="#" class="logo flex items-center gap-2 md:gap-3 p-2">
        <img src="@/assets/logo.svg" class="w-8 md:w-10 xl:w-12" />
        <span
          class="text-gradient font-semibold text-2xl md:text-4xl self-center"
          >To-Do List</span
        >
      </a>
      <a href="#" class="hidden md:block p-2 text-magic text-lg">Home</a>
      <a href="#" class="hidden md:block p-2 text-magic text-lg">About</a>
      <a href="#" class="hidden md:block p-2 text-magic text-lg">Logout</a>
    </div>

    <div class="flex align-middle gap-1">
      <p class="p-2 text-user cursor-default text-md md:text-lg">
        test@gmail.com
      </p>
    </div>
  </nav>
</template>
