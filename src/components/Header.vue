<template>
    <header class="container mx-auto mt-6 flex flex-col gap-3">
        <img class="mx-auto" :src="item.values['c-l7DcP3ny0V']" width="150">
        <h1 class="text-center text-2xl font-semibold cursor-default text-gray-700 mb-4" >لیست محصولات فروشگاه {{ item.name }}</h1>
        <input type="text" class="outline-none px-3 py-2 my-4 border rounded-lg focus:ring-red-200 focus:ring-2 focus:border-red-500"
        placeholder="نام محصول مورد نظرتان را وارد کنید ...">
    </header>
</template>

<script>
export default {
    props:{
        item: Object,
    }
}
</script>

<style>

</style>