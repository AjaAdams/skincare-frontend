<template>
  <div class="products">
    <h1>{{ message }}</h1>
    <div v-for="product in products">
      <router-link v-bind:to="`/products/${product.id}`">
        <img v-bind:src="product.image" v-bind:alt="product.name">
      </router-link>
        <h2>{{product.brand}}</h2>
        <h3>{{product.name}}</h3>
    </div>

  </div>
</template>

<style>
  img {
    width: 175px;
  }
</style>

<script>
import axios from "axios"

export default {
  data: function() {
    return {
      message: "Welcome to Products!",
      products: []
    };
  },
  created: function() {
    axios
      .get("/api/products")
      .then(response => {
        console.log("Product Index", response);
        this.products = response.data
      })
  },
  methods: {}
};
</script>