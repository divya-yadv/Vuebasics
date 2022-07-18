<template>
  <div>
    <header class="top-bar spread">
      <nav class="top-bar-nav">
        <router-link to="/" class="top-bar-link">
          <i class="icofont-spoon-and-fork"></i>
          <span>Home</span>
        </router-link>
        <router-link to="/products" class="top-bar-link">
          <span>Products</span>
        </router-link>
        <router-link to="/past-orders" class="top-bar-link">
          <span>Past Orders</span>
        </router-link>
      </nav>
      <!-- toggle view by clicking on cart button -->
      <span @click="toggleView" class="top-bar-cart-link">
        <i class="icofont-cart-alt icofont-1x"></i>
        <span>Cart({{ totalQuantity }})</span>
      </span>
    </header>
    <router-view :inventory="inventory" :addToCart="addToCart" />
    <Sidebar v-if="showSideBar" :toggle="toggleView" :cart="cart" :inventory="inventory" :remove="removeItem" />
  </div>
</template>

<script>
import Sidebar from '@/components/Sidebar.vue'
import food from './food.json'
export default {
  componets: {
    Sidebar
  },
  data() {
    return {
      showSideBar: true,
      inventory: food,
      cart: {}
    }
  },
  computed: {
    totalQuantity() {
      const total = Object.values(this.cart).reduce((acc, item, index) => {
        return acc + item;
      }, 0)
      return total;
    }
  },
  methods: {
    addToCart(name, quantity) {
      //  receive type and number and then increase it
      if (!this.cart[name]) {
        this.cart[name] = 0;
      }
      this.cart[name] += quantity;
      console.log(this.cart);
    },
    toggleView() {
      return this.showSideBar = !this.showSideBar;
    },
    removeItem(item) {
      delete this.cart[item];
    }
  }
}
</script>

<!-- <style>
body {
  margin: 0px;
  padding: 0px;
}
</style> -->