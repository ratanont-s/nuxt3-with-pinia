<template>
  <div>
    <h2 class="text-white text-2xl text-center my-8">All Products</h2>
    <ul class="grid grid-cols-2 gap-7">
      <li v-for="(product, index) in products" :key="index">
        <ProductCard :product="product" />
      </li>
    </ul>
  </div>
</template>

<script setup>
const { data: products } = await useFetch('http://localhost:4000/products')
</script>

<style scoped></style>