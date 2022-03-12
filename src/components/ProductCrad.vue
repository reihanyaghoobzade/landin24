<template>
    <div class="border rounded-lg p-4 flex sm:flex-col gap-3">
      <img :src="cardItem['c-WoMta3EdKU']" alt="" class="block mx-auto h-36 sm:h-52">
      <div class="flex flex-col justify-around gap-3">
        <h3 class="font-semibold text-lg text-gray-700">{{ cardItem['c-zNhlqGccUo'] }}</h3>
        <p class="font-light text-gray-600">{{ cardItem['c-ehIiJHuNqx'] }}</p>
        <div class="flex justify-between">
            <a :href="`tel:${phoneNumber.values['c-BdNc0saeof']}`" class="bg-red-500 hover:bg-red-600 text-white rounded-full py-1 px-4">سفارش</a>
            <div class="flex items-center gap-1">
                <span>{{ cardItem['c-GMAP2hhQnB'] }}</span>
                <img src="../assets/Images/Toman.svg" width="18">
            </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  props:{
    cardItem: Object,
    phoneNumber: Object,
  },
}
</script>

<style>

</style>