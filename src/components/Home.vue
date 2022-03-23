<template>
  <div v-if="cardsLoading" class="flex-1 my-20">
    <div class="w-10 h-10 border-4 border-red-600 border-t-transparent border-solid rounded-full animate-spin mx-auto"></div>
  </div>
  <main v-else class="flex-1 mx-2 sm:mx-0">
    <div class="flex-1 mb-16">
      <section class="container mx-auto">
        <div class="grid sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-4 my-6">
            <ProductCard v-for="item in cardItems" :key="item.index" :cardItem="item.values" :phoneNumber="brandItems[0]"></ProductCard>
        </div>
      </section>
    </div>
  </main>
</template>

<script setup>
import ProductCard from "./ProductCrad.vue";
import { inject } from "vue";

const brandItems = inject("brandItems");
const cardItems = inject("cardItems");
const cardsLoading = inject("cardsLoading");
</script>

<style>
</style>