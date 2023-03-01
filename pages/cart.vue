<template>
  <div>
    <h2 class="text-white text-2xl text-center my-8">Your Basket</h2>

    <ul class="card text-xl" v-if="cartStore.cart.length">
      <!-- Product list -->
      <li v-for="product in cartStore.cart" class="grid grid-cols-6 gap-8 items-center py-4">
        <img :src="product.image" :alt="product.title" class="aspect-square object-contain">
        <h5 class="col-span-2">{{ product.title }}</h5>
        <!-- product quantity -->
        <ProductQuantity :product="product" class="" />
        <p class="">{{ Math.ceil(product.price * product.quantity) }} coins</p>

        <!-- Delete -->
        <button class="" @click="cartStore.deleteFromCart(product)">
          <span class="material-symbols-outlined">delete</span>
        </button>
      </li>

      <!-- Cart total -->
      <li class="text-right pt-4 mt-4 border-t-2">
        <span>Tota amount to pay: </span>
        <span class="text-primary text-2xl">{{ Math.ceil(cartStore.cartTotal) }}</span>
      </li>
    </ul>

    <div v-else>
      <p class="text-white">There are not items in your basket.</p>
    </div>

  </div>
</template>

<script setup>
import { useCartStore } from '~~/stores/cartStore';

const cartStore = useCartStore()
</script>

<style scoped></style>