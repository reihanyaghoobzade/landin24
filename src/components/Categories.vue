<template>
    <div class=" container mx-auto my-10 flex gap-8">
        <a href="#" v-for="item in categoryItems" :key="item.index" @click="filterSearch(item.name)" class="inline-flex">{{ item.name }}</a>
    </div>
</template>

<script setup>
import { ref, inject } from 'vue';

const filter = ref([]);
const categoryItems = inject("categoryItems");
const cardItems = inject("cardItems");

function filterSearch(name){
    const card = document.querySelectorAll('.card');
    card.forEach(element => element.classList.add("hidden"));
    !filter.value.includes(name) && filter.value.push(name);
    filter.value.map(element => {
        for (let i = 0; i < cardItems.value.length; i++) {
            console.log(cardItems.value[i].values['c-DXR1PG-fhS']);
            cardItems.value[i].values['c-DXR1PG-fhS'] === element &&
                card[i].classList.remove("hidden");
        }
    });
}

</script>

<style>

</style>