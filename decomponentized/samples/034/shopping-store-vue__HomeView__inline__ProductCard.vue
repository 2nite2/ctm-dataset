<script setup lang="ts">
import { onMounted, ref } from 'vue';
import { storeToRefs } from 'pinia';
import { watchDebounced } from '@vueuse/core';

import { useProductsStore } from '@/stores/products';
import { useCurrencyFormatter } from '@/composables/currencyFormatter';


const productsStore = useProductsStore();
const currencyFormatter = useCurrencyFormatter();
const { products } = storeToRefs(productsStore);

let isLoading = ref(false);
const searchInput = ref("");

onMounted(async () => {
  isLoading.value = true;
  await productsStore.fetchProducts();
  isLoading.value = false;
});

watchDebounced(searchInput, async () => {
  isLoading.value = true;
  await productsStore.searchProducts(searchInput.value);
  isLoading.value = false;
}, {
  debounce: 500,
  maxWait: 4000,
});

</script>

<template>
  <main class="container max-w-5xl mx-auto p-4 pb-8">

    <div class="text-sm breadcrumbs mb-6">
      <ul>
        <li><RouterLink to="/">Home</RouterLink></li>
        <li>Products</li>
      </ul>
    </div>
    
    <input type="text" v-model="searchInput" placeholder="Search products..." class="input input-bordered mb-4 w-full max-w-md" />

    <div class="flex justify-center p-8" v-if="isLoading"><span class="loading loading-spinner loading-lg"></span></div>
    
    <div class="text-center p-8" v-if="!isLoading && !products.length">
      <div>No products found.</div>
      <div class="text-gray-600 text-sm mt-4">Try searching for something else.</div>
    </div>
    
    <div class="grid gap-4 grid-cols-1 sm:grid-cols-2 md:grid-cols-3" v-if="!isLoading && products.length">
      <div
        v-for="product in products"
        :key="product.id"
        class="rounded-lg shadow overflow-hidden bg-base-100"
      >
            <div class="w-full h-48 relative">
              <div class="absolute animate-pulse flex items-center justify-center w-full h-full mb-4 bg-gray-300 dark:bg-gray-700">
                <svg class="w-10 h-10 text-gray-200 dark:text-gray-600" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 16 20">
                  <path d="M14.066 0H7v5a2 2 0 0 1-2 2H0v11a1.97 1.97 0 0 0 1.934 2h12.132A1.97 1.97 0 0 0 16 18V2a1.97 1.97 0 0 0-1.934-2ZM10.5 6a1.5 1.5 0 1 1 0 2.999A1.5 1.5 0 0 1 10.5 6Zm2.221 10.515a1 1 0 0 1-.858.485h-8a1 1 0 0 1-.9-1.43L5.6 10.039a.978.978 0 0 1 .936-.57 1 1 0 0 1 .9.632l1.181 2.981.541-1a.945.945 0 0 1 .883-.522 1 1 0 0 1 .879.529l1.832 3.438a1 1 0 0 1-.031.988Z"/>
                  <path d="M5 5V.13a2.96 2.96 0 0 0-1.293.749L.879 3.707A2.98 2.98 0 0 0 .13 5H5Z"/>
                </svg>
              </div>
              <RouterLink :to="`/products/${product.id}`"><img class="w-full h-full absolute object-cover z-[1]" :src="product.images[0]" alt="Product Image" /></RouterLink>
            </div>
            <div class="p-4">
              <RouterLink :to="`/products/${product.id}`" class="font-medium mb-2 line-clamp-1">{{ product.title }}</RouterLink>
              <div class="flex justify-between items-center text-gray-600">
                <span class="">{{ currencyFormatter.format(product.price) }}</span>
                <span class="text-sm">{{ parseFloat(product.rating.toString()).toFixed(2) }} ★</span>
              </div>
            </div>
          </div>
    </div>
    
  </main>
</template>
