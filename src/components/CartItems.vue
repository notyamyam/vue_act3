<template>
  <div class="d-flex flex-column">
    <div class="d-flex flex-column col-md-6 mt-4">
      <h3>My Cart</h3>
      <h6>Total Price: ₱ {{ totalPrice ? totalPrice.toFixed(2) : "0.00" }}</h6>
    </div>

    <div class="row">
      <template v-if="cart.length === 0">
    <div class="col-md-12">
      <p>The cart is empty.</p>
    </div>
  </template>
  <template v-else>
    <div class="cart-item" v-for="(item, index) in cart" :key="index">
      <div class="d-flex align-items-center justify-content-between">
        <div>
          <h5>{{ item.name }}</h5>
          <p>Price: ₱{{ item.price }}</p>
          <h6>Quantity: {{ item.quantity }}</h6>
        </div>
        <div>
          <button class="btn btn-danger" @click="removeFromCart(index)">
            Remove
          </button>
          <button @click="incrementQuantity(index)">+</button>
          <button @click="decrementQuantity(index)">-</button>
        </div>
      </div>
    </div>
  </template>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cart: Array,
    incrementQuantity: Function,
    decrementQuantity: Function,
    removeFromCart: Function,
    totalPrice: Function,
  },
};
</script>

<style>
.cart-item {
  border: 1px solid #ccc;
  margin-bottom: 10px;
  padding: 20px;
  border-radius: 15px;
}
</style>
