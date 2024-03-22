<template>
  <div class="container">
    <div class="row">
      <div class="col-md-4" v-for="(product, index) in products" :key="index">
        <div class="product d-flex flex-column">
          <div>
            <h3>{{ product.name }}</h3>
            <p>Price: ₱{{ product.price }}</p>
          </div>
          <button class="btn btn-primary" @click="addToCart(product)">
            Add to Cart
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    products: Array, // Accepts the products array as a prop
    addToCart: Function,
  },
};
</script>

<style>
.product {
  border: 1px solid #ccc;
  margin-bottom: 10px;
  padding: 10px;
  border-radius: 15px;
}
</style>
