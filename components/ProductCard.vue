<template>
  <div class="card grid grid-cols-3 gap-x-7">
    <div>
      <img :src="product.image" :alt="product.title" class="aspect-square object-contain">
    </div>
    <div class="col-span-2 flex flex-col">
      <h5 class="text-primary text-xl truncate">{{ product.title }}</h5>
      <p class="truncate">{{ product.description }}</p>
      <p class="text-xl text-primary mb-3">{{ product.price }} Silver coins</p>
      <div class="mt-auto text-right">
        <button class="btn" @click="addToBasket()" :disabled="isPending">
          <span v-show="!isPending">Add to Basket</span>
          <span v-show="isPending">Adding...</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { useCartStore } from '~~/stores/cartStore';

const { product } = defineProps(['product'])

const cartStore = useCartStore()
const isPending = ref(false)

const addToBasket = async () => {
  isPending.value = true
  await cartStore.addToCart(product)
  setTimeout(() => {
    isPending.value = false
  }, 1000)
}
</script>

<style scoped></style>
