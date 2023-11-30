<script lang="ts" setup>
definePageMeta({
  layout: "blank",
});
</script>

<template>
  <section class="bg-gradient-to-br from-blue-500 via-blue-600 to-indigo-700 min-h-screen flex items-center">
    <div class="container mx-auto">
      <div class="flex justify-center">
        <NuxtLink
          to="/"
          class="absolute top-4 left-4 bg-white text-blue-600 h-12 w-12 flex justify-center items-center rounded-full shadow-lg cursor-pointer"
        >
          <i class="ri-arrow-left-line"></i>
        </NuxtLink>
      </div>
      <div class="bg-glow p-8 rounded-lg shadow-md w-full max-w-md mx-auto">
        <Login />
      </div>
    </div>
  </section>
</template>

<style scoped>
  .bg-gradient-to-br {
    background: linear-gradient(to bottom right, #3182ce, #4c51bf);
  }

  .container {
    max-width: 600px;
  }

  .ri-arrow-left-line {
    font-size: 1.5rem;
  }

  .bg-white {
    background-color: #ffffff;
  }

  .shadow-md {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .rounded-lg {
    border-radius: 1rem;
  }

  .p-8 {
    padding: 2rem;
  }

  .text-blue-600 {
    color: #3182ce;
  }

  .h-12 {
    height: 3rem;
  }

  .w-12 {
    width: 3rem;
  }

  .flex {
    display: flex;
  }

  .justify-center {
    justify-content: center;
  }

  .items-center {
    align-items: center;
  }

  .bg-glow {
    /* Menambahkan efek glow dengan warna hijau, merah, dan ungu */
    box-shadow: 0 0 20px rgba(0, 255, 0, 0.8),
                0 0 20px rgba(255, 0, 0, 0.8),
                0 0 20px rgba(128, 0, 128, 0.8);
  }
</style>
