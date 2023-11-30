<script lang="ts" setup>
import type { Products } from "~/types/products";

definePageMeta({
  middleware: ["user-access"],
});

const products = ref<Products[]>([]);
const totalPrice = computed(() => {
  return products.value
    .filter((product) => product.price !== undefined)
    .reduce((accumulator, currentValue) => accumulator + currentValue.price!, 0);
});

onMounted(() => {
  let localStorageData = localStorage.getItem("products");
  if (localStorageData) {
    products.value = JSON.parse(localStorageData);
  }
});

const removeCart = (id: number) => {
  products.value = products.value.filter((item) => item.id !== id);
  localStorage.setItem("products", JSON.stringify(products.value));
};
</script>

<template>
  <section class="bg-gray-100 min-h-screen py-12">
    <div class="container mx-auto">
      <div class="flex justify-between items-center mb-12">
        <h1 class="text-4xl font-bold">Shopping Cart</h1>
        <p class="text-2xl font-semibold">{{ products.length }} Items</p>
      </div>

      <div class="flex">
        <div class="w-3/4 pr-8">
          <div v-if="products.length > 0" class="grid grid-cols-1 gap-6">
            <template v-for="(item, index) in products" :key="index">
              <CardsCardCart :product="item" @removeCart="removeCart" />
            </template>
          </div>
          <div v-else>
            <h5 class="text-xl font-light text-center">Cart is empty</h5>
          </div>
        </div>

        <div class="w-1/4 bg-white p-6 rounded-lg shadow-md">
          <h3 class="text-xl font-medium mb-6">Order Summary</h3>

          <div v-if="products.length > 0">
            <div class="grid grid-cols-2 gap-4">
              <template v-for="(item, index) in products" :key="index">
                <div class="flex items-center">
                  <span class="text-sm">{{ item.name }}</span>
                  <span class="text-sm font-semibold">${{ item.price }}</span>
                </div>
              </template>
            </div>
          </div>
          <div v-else>
            <p class="text-sm text-center font-light">
              There are no orders yet
            </p>
          </div>

          <div class="pt-4 flex items-center justify-between mb-6">
            <span class="text-base">Total</span>
            <span class="text-base font-bold">${{ totalPrice }}</span>
          </div>

          <button class="bg-blue-600 text-white text-base font-bold w-full py-2 rounded-lg hover:bg-blue-700">
            Checkout
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
  /* Custom styles for the cart page */

  .container {
    max-width: 1200px;
    margin-left: auto;
    margin-right: auto;
  }

  .cart-section {
    background-color: #f8fafc;
    min-height: 100vh;
    padding: 40px 0;
  }

  .cart-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }

  .cart-title {
    font-size: 2rem;
    font-weight: bold;
  }

  .cart-items {
    display: grid;
    grid-template-columns: 1fr;
    gap: 20px;
  }

  .cart-empty {
    text-align: center;
    font-size: 1.5rem;
    font-weight: light;
  }

  .order-summary {
    background-color: #ffffff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }

  .summary-title {
    font-size: 1.5rem;
    font-weight: bold;
    margin-bottom: 1rem;
  }

  .summary-details {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-bottom: 1rem;
  }

  .total-price {
    display: flex;
    justify-content: space-between;
    font-size: 1.25rem;
    font-weight: bold;
  }

  .checkout-btn {
    background-color: #1e40af;
    color: #ffffff;
    font-size: 1.25rem;
    font-weight: bold;
    padding: 12px;
    width: 100%;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .checkout-btn:hover {
    background-color: #1c3faa;
  }
</style>
