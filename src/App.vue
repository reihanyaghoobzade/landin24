<script setup>
import { RouterLink, RouterView } from "vue-router";
import { ref, provide } from "vue";
import Header from "./components/Header.vue";
import Categories from "./components/Categories.vue";
import Footer from "./components/Footer.vue";
const docId = "r3wHCIbocr";
const brandTableId = "grid-5s_DTzk4lU";
const cardsTableId = "grid-OxkfyQYjSp";
const categoryTableId = "grid-QvGnUIqLrZ";
const token = "d5b1f114-1d0a-45af-9138-d6b75d520488";
const brandUrl = `https://coda.io/apis/v1/docs/${docId}/tables/${brandTableId}/rows`;
const cardsUrl = `https://coda.io/apis/v1/docs/${docId}/tables/${cardsTableId}/rows`;
const categoryUrl = `https://coda.io/apis/v1/docs/${docId}/tables/${categoryTableId}/rows`;
const cardsLoading = ref(true);
const brandItems = ref([]);
const cardItems = ref([]);
const categoryItems = ref([]);

function getData(url, res, loading = ref(null)) {
  fetch(url, {
    method: "GET",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer ${token}`,
    },
  })
    .then((response) => response.json())
    .then((data) => {
      res.value = data.items;
      loading.value = false;
    })
    .catch((error) => {
      console.error("Error: ", error);
    });
}

getData(brandUrl, brandItems);
getData(cardsUrl, cardItems, cardsLoading);
getData(categoryUrl, categoryItems);

provide("brandItems", brandItems);
provide("cardItems", cardItems);
provide("cardsLoading", cardsLoading);
provide("categoryItems", categoryItems);
</script>

<template>
  <Header :item="brandItems[0]" />
  <Categories />
  <router-view></router-view>
  <Footer :item="brandItems[0]" />
</template>

<style>
</style>
