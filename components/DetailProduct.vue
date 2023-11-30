<script setup lang="ts">
const props = defineProps({
  product: {
    type: Object,
    default: {},
  },
});
</script>
<template>
  <section class="py-10">
    <div class="container">
      <NuxtLink
        to="/product"
        class="bg-white border border-slate-300 w-max flex items-center gap-1 py-2 px-5 rounded-full mb-7 cursor-pointer"
      >
        <i class="ri-arrow-left-s-line text-base font-medium"></i>
        <span class="text-base font-medium">Kembali</span>
      </NuxtLink>
      <div class="flex items-center">
        <div
          class="w-1/2 bg-gray-300 mr-5 rounded-3xl flex justify-center items- center p-5 h-[500px]"
        >
          <img
            :src="props.product.image"
            class="w-full h-full object-contain"
          />
        </div>
        <div class="w-1/2 pl-5">
          <p class="text-xl font-light mb-3">{{ props.product.category }}</p>
          <h1 class="text-4xl font-bold mb-3">{{ props.product.name }}</h1>
          <p class="mb-10">{{ props.product.description }}</p>
          <div class="flex flex-col gap-4">
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
}

.product-image-container {
  width: 50%;
  background-color: #f3f4f6;
  margin-right: 2rem;
  border-radius: 1.5rem;
  overflow: hidden;
}

.product-image {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.product-details {
  width: 50%;
  padding-left: 2rem;
}

.back-button {
  background-color: #fff;
  border: 1px solid #cbd2d9;
  color: #4a5568;
  display: inline-flex;
  align-items: center;
  gap: 1;
  padding: 0.5rem 1rem;
  border-radius: 999px;
  transition: background-color 0.3s ease;
}

.back-button:hover {
  background-color: #edf2f7;
}

.product-category {
  font-size: 1.25rem;
  font-weight: 300;
  margin-bottom: 1rem;
  color: #4a5568;
}

.product-name {
  font-size: 2.5rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: #1a202c;
}

.product-price {
  font-size: 2rem;
  font-weight: 300;
  margin-bottom: 1rem;
  color: #2d3748;
}

.product-description {
  margin-bottom: 2rem;
  color: #4a5568;
}

.add-to-cart-button {
  background-color: #1a202c;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  border-radius: 999px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.add-to-cart-button i {
  margin-right: 0.5rem;
}

.add-to-cart-button:hover {
  background-color: #2d3748;
}
</style>
