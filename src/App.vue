<script setup></script>

<template>
  <nav class="mb-5 p-5 justify-between flex flex-wrap">
    <div class="flex flex-row items-center gap-2">
      <a href="#" class="logo flex items-center gap-1 p-2">
        <img src=" ./assets/logo.svg" width="35"/>
        <span>Todo List App</span>
      </a>
      <a href="#" class="p-2">Home</a>
      <a href="#" class="p-2">About</a>
      <a href="#" class="p-2">Logout</a>
    </div>
    <div>
      <p class="p-2">test@gmail.com</p>
    </div>
  </nav>

  <main class="p-5">

    <!-- <div>
      <div>Todo title is required!</div>
      <div>
        <i>X</i>
      </div>
    </div> -->

    <section class="px-6 py-3">

      <form class="mt-3 mb-6 flex justify-between items-center">
        <div>
          <input class=" border-1 border-solid" type="text" name="todo" id="todo"/>
        </div>
        <div>
          <button class="py-2 px-8">Add Todo</button>
        </div>
      </form>

      <ul class="gap-3 flex flex-col">
        <li class="todo py-2 px-3 flex justify-between">
            <p>Todo Title 1</p>
            <div>
              <button class="py-1 px-3">X</button>
            </div>
        </li>

        <li class="todo py-2 px-3 flex justify-between">
            <p>Todo Title 1</p>
            <div>
              <button class="py-1 px-3">X</button>
            </div>
        </li>

        <li class="todo py-2 px-3 flex justify-between">
            <p>Todo Title 1</p>
            <div>
              <button class="py-1 px-3">X</button>
            </div>
        </li>
      </ul>

    </section>
  </main>
</template>

<style scoped>
</style>
