<script setup></script>

<template>
  <nav class="mb-2 p-2 md:mb-5 md:p-5">
    
    <div class="flex flex-row items-center gap-4">
      <a href="#" class="logo flex items-center gap-2 md:gap-3 p-2">
        <img src="./assets/logo.svg" class="w-7 md:w-10 xl:w-12"/>
        <span class="text-gradient font-semibold text-2xl md:text-4xl self-center">Todo List</span>
      </a>
      <a href="#" class="hidden md:block p-2 text-magic text-lg">Home</a>
      <a href="#" class="hidden md:block p-2 text-magic text-lg">About</a>
      <a href="#" class="hidden md:block p-2 text-magic text-lg">Logout</a>
    </div>

    <div class="flex align-middle gap-1">
      <p class="p-2 text-user text-md md:text-lg">test@gmail.com</p>

    </div>

  </nav>

  <main class="px-2 pt-5 md:pt-10 md:px-8 lg:px-20 xl:px-32">

    <!-- <div>
      <div>Todo title is required!</div>
      <div>
        <i>X</i>
      </div>
    </div> -->

    <section class="px-6 py-3">

      <form class="mt-3 mb-12 flex flex-col justify-center items-end md:flex-row md:justify-between md:items-center">
        <div class="border-gradient w-[100%]  md:w-[70%] xl:w-[80%]">
          <input class="todo-input" type="text" name="todo" id="todo"/>
        </div>
        <div>
          <button class="btn mt-6 md:mt-0">Add Todo</button>
        </div>
      </form>

      <ul class="gap-5 flex flex-col">
        <li class="todo">
          <p>Todo Title 1</p>
          <div>
            <button class="btn-danger">
              <i class="bi bi-trash"></i>
            </button>
          </div>
        </li>

        <li class="todo">
          <p>Todo Title 2</p>
          <div>
            <button class="btn-danger">
              <i class="bi bi-trash"></i>
            </button>
          </div>
        </li>

        <li class="todo">
          <p>Todo Title 3</p>
          <div>
            <button class="btn-danger">
              <i class="bi bi-trash"></i>
            </button>
          </div>
        </li>
      </ul>

    </section>
  </main>
</template>