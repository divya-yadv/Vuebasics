<template>
  <main class="wrapper">
    <h1>Products</h1>
    <div class="card-container">
      <ProductCard v-for="(item) in inventory" :key="item.id" :item="item" :addToCart="addToCart" />
    </div>
  </main>
</template>

<script>
import ProductCard from '@/components/ProductCard.vue'
export default {
  name: 'Products',
  components: {
    ProductCard
  },
  props: ['inventory', 'addToCart']
}

</script>