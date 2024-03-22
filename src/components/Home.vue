<template>
  <div class="d-flex flex-column justify-content-center align-items-center p-4">
    <div class="container">
      <div class="row">
        <ProductListing
          :products="products"
          :addToCart="addToCart"
        />
      </div>
    </div>

    <div class="container mt-4">
      <CartItems
        :cart="cart"
        :removeFromCart="removeFromCart"
        :incrementQuantity="incrementQuantity"
        :decrementQuantity="decrementQuantity"
        :totalPrice="totalPrice"
      />
    </div>
  </div>

  <RouterView />
</template>

<script>
import { RouterLink, RouterView } from "vue-router";
import ProductListing from "./ProductListing.vue";
import CartItems from "./CartItems.vue";

export default {
  components: {
    ProductListing,
    CartItems,
  },
  data() {
    return {
      products: [
        { name: "Titan T-Shirt", price: 200 },
        { name: "Nike Short", price: 300 },
        { name: "Addidas DRose", price: 4000 },
        { name: "Nike Kd 5", price: 6000 },
        { name: "Asics Wrist Band", price: 400 },
        { name: "Nike Sando", price: 300 },
        { name: "Puma Running Shoes", price: 2500 },
        { name: "Under Armour Hoodie", price: 1500 },
        { name: "Reebok Leggings", price: 800 },
        { name: "New Balance Cap", price: 200 },
        { name: "Adidas Soccer Ball", price: 1000 },
        { name: "Nike Backpack", price: 1200 },
      ],
      cart: [],
    };
  },
  methods: {
    addToCart(product) {
      const checkToken = localStorage.getItem("token");
      if (checkToken) {
        const existingItem = this.cart.find(
          (item) => item.name === product.name
        );
        if (existingItem) {
          existingItem.quantity++;
        } else {
          this.cart.push({ ...product, quantity: 1 });
        }
      } else {
        this.$router.push("/login");
      }
    },
    removeFromCart(index) {
      this.cart.splice(index, 1);
    },
    incrementQuantity(index) {
      this.cart[index].quantity++;
    },
    decrementQuantity(index) {
      if (this.cart[index].quantity > 1) {
        this.cart[index].quantity--;
      }
    },
  },

  computed: {
    totalPrice() {
      return this.cart.reduce(
        (total, item) => total + item.price * item.quantity,
        0
      );
    },
  },
};
</script>
