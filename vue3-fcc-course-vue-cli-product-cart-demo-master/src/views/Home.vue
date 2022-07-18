<template>
  <div class="home">
    <div class="splash-container">
      <div class="splash">
        <h1>Splendid Food</h1>
      </div>
    </div>

    <main class="wrapper">
      <h2>Recommended</h2>

      <div class="recommended">
        <!-- add loop for 3 items and update fields accordingly -->
        <ProductCard v-for="(item) in inventory.slice(0, 3)" :key="item.id" :item="item" :addToCart="addToCart" />
      </div>

    </main>
  </div>
</template>

<script>
import ProductCard from '@/components/ProductCard.vue'
export default {
  name: 'Home',
  components: {
    ProductCard
  },
  props: ['inventory', 'addToCart']
}

</script>
