<template>
  <aside class="cart-container">
    <div class="cart">
      <h1 class="cart-title spread">
        <span>
          Cart
          <i class="icofont-cart-alt icofont-1x"></i>
        </span>
        <button @click="toggle" class="cart-close">&times;</button>
      </h1>

      <div class="cart-body">
        <table class="cart-table">
          <thead>
            <tr>
              <th><span class="sr-only">Product Image</span></th>
              <th>Product</th>
              <th>Price</th>
              <th>Qty</th>
              <th>Total</th>
              <th><span class="sr-only">Actions</span></th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(quantity, key, i) in cart" :key="i">
              <td><i class="icofont- icofont-3x"></i></td>
              <td>{{ key }}</td>
              <td>${{ getPrice(key) }}</td>
              <td class="center">{{ quantity }}</td>
              <td>${{ getPrice(key) * quantity }}</td>
              <td class="center">
                <button @click="remove(key)" class="btn btn-light cart-remove">
                  &times;
                </button>
              </td>
            </tr>
          </tbody>
        </table>
        <p class="center"><em v-if="Object.keys(cart).length === 0">No items in cart</em></p>
        <div class="spread">
          <span><strong>Total:</strong> ${{ cartTotal() }}</span>
          <button class="btn btn-light">Checkout</button>
        </div>
      </div>
    </div>
  </aside>
</template>

<script>
export default {
  name: 'Sidebar',
  props: ['toggle', 'cart', 'inventory', 'remove'],
  methods: {
    getPrice(key) {
      const product = this.inventory.find((product) => {
        return product.name === key;
      });
      return product.price.USD;
    },
    cartTotal() {
      // const names = Object.keys(this.cart);
      const total = Object.entries(this.cart).reduce((acc, curritem, index) => {
        return acc + (curritem[1] * this.getPrice(curritem[0]));
      }, 0)
      return total.toFixed(2);
    }
  }
}
</script>