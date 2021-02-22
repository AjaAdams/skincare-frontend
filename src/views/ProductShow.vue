<template>
  <div class="products-show">
    <h1>{{ product.name }}</h1>
    <img v-bind:src="product.image" v-bind:alt="product.name"> <br><br>

    <router-link to="/products">Back to Products</router-link>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios"

export default {
  data: function() {
    return {
      product: {},
      message: "Welcome to Vue.js!",
      errors: [],
      isLoaded: false
    };
  },
  created: function() {
    axios
      .get("/api/products/" + this.$route.params.id)
      .then(response => {
        console.log("product show", response);
        this.product = response.data;
        this.isLoaded = true;
      })
      .catch(error => {
        console.log("product show error", error.response)
      });
  },
  methods: {}
};
</script>