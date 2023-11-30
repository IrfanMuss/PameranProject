<script lang="ts" setup>
import { useProductsStore } from "~/stores/products";

definePageMeta({
  middleware: ["user-access"],
});

const productStore = useProductsStore();
const allProducts = ref([]);

productStore.getAllProducts().then(() => {
  allProducts.value = productStore.products;
});

const selectedCategory = ref("");
</script>
<template>
  <div class="piw">
    <section>
      <div class="container">
        <div class="py-10">
          <div class="mb-6 flex justify-center items-center gap-6">
            <NuxtLink
              to="/category/create"
              class="bg-orange-500 text-white flex justify-center items-center px-3 rounded-lg"
            >➕ Kategori
            </NuxtLink>
            <NuxtLink
              to="/product/create"
              class="bg-green-500 text-white flex justify-center items-center px-3 rounded-lg"
            >➕ Project
            </NuxtLink>
            <Dropdown @selected-category="selectedCategory = $event" />
          </div>
          <div class="flex gap-6 flex-wrap mx-auto">
            <template v-for="(item, index) in allProducts" :key="index">
              <CardsCardProduct :product="item" class="w-[calc(100%/4-18px)]" />
            </template>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
}

.py-10 {
  padding-top: 2.5rem;
  padding-bottom: 2.5rem;
}

.mb-6 {
  margin-bottom: 1.5rem;
}

.flex {
  display: flex;
}

.items-center {
  align-items: center;
}

.gap-6 {
  gap: 1.5rem;
}

.bg-orange-500 {
  background-color: #ff8c00;
}

.bg-green-500 {
  background-color: #00cc00;
}

.text-white {
  color: #fff;
}

.px-3 {
  padding-left: 0.75rem;
  padding-right: 0.75rem;
}

.rounded-lg {
  border-radius: 0.375rem;
}

.flex-wrap {
  flex-wrap: wrap;
}
</style>
