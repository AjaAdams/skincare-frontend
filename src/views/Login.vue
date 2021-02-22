<template>
  <div class="login">
    <h1>Welcome to Routine.me</h1>
    <label for="username">Username </label>
    <input 
      type="text"
      id="username"
      v-model="username"
    /><br><br>
    <label for="password">Password </label>
    <input 
      type="text"
      id="password"
      v-model="password"
    />
  </div>
</template>

<style>
</style>

<script>
import axios from "axios"

export default {
  data: function() {
    return {
      username: "",
      password: "",
      errors: []
    };
  },
  created: function() {},
  methods: {}
};
</script>