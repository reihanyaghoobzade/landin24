<template>
    <Header :item="brandItems[0]"/>
    <div v-if="loading" class="flex-1 my-20">
      <div class="w-10 h-10 border-4 border-red-600 border-t-transparent border-solid rounded-full animate-spin mx-auto"></div>
    </div>
    <main v-else class="flex-1 mx-2 sm:mx-0">
      <div class="flex-1">
        <section class="container mx-auto grid sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-3 my-6">
                <ProductCard v-for="item in cardItems" :key="item.index" :cardItem="item.values" :phoneNumber="brandItems[0]"></ProductCard>
        </section>
      </div>
    </main>
    <Footer :item="brandItems[0]"/>
</template>

<script>
import ProductCard from "../components/ProductCrad.vue";
import Header from "../components/Header.vue";
import Footer from "../components/Footer.vue";
import { ref } from "vue";
import axios from "axios";
export default {
  components: {
    Header,
    ProductCard,
    Footer,
  },
  setup() {
    const docId = "r3wHCIbocr";
    const brandTableId = "grid-5s_DTzk4lU";
    const cardsTableId = "grid-OxkfyQYjSp";
    const token = "d5b1f114-1d0a-45af-9138-d6b75d520488";
    const brandUrl = `https://coda.io/apis/v1/docs/${docId}/tables/${brandTableId}/rows`;
    const cardsUrl = `https://coda.io/apis/v1/docs/${docId}/tables/${cardsTableId}/rows`;
    const loading = ref(true);
    const brandItems = ref([]);
    const cardItems = ref([]);

    function getBrandData() {
      axios.get(brandUrl, {
          headers: {
              'Content-Type': 'application/json',
              'Authorization': `Bearer ${token}`,
          },
          })
          .then((response) => {
          brandItems.value = response.data.items;
          loading.value = true;
          })
          .catch((error) => console.log(error));
      }


    function getCardsData() {
      axios
        .get(cardsUrl, {
          headers: {
            'Content-Type': 'application/json',
            'Authorization': `Bearer ${token}`,
          },
        })
        .then((response) => {
          cardItems.value = response.data.items;
          loading.value = false;
        })
        .catch((error) => console.log(error));
    }

    getBrandData();
    getCardsData();

    return { loading, brandItems, cardItems }
  },
};
</script>

<style>
</style>