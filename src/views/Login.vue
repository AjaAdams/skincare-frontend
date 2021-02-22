<template>
  <div class="login">
    <form v-on:submit.prevent="submit()">
      <h1>Welcome to Routine.me</h1>
      <h2>Sign In</h2>
      <ul>
        <li class="text-danger" v-for="error in errors">{{ error }}</li>
      </ul>
      <div class="form-group">
        <label>Email: </label>
        <input type="email" class="form-control" v-model="email">
      </div>
      <div class="form-group">
        <label>Password: </label>
        <input type="password" class="form-control" v-model="password">
      </div> <br>
      <input type="submit" class="btn btn-primary" value="Submit">
      
      <h4>Need an account?</h4>
    </form>
  </div>
</template>


<style>
</style>

<script>
import axios from "axios"

export default {
  data: function() {
    return {
      email: "",
      password: "",
      errors: []
    };
  },
  created: function() {},
  methods: {
    submit: function() {
      var params = {
        email: this.email,
        password: this.password
      };
      axios
        .post("/api/sessions", params)
        .then(response => {
          axios.defaults.headers.common["Authorization"] =
            "Bearer " + response.data.jwt;
          localStorage.setItem("jwt", response.data.jwt);
          this.$router.push("/");
        })
        .catch(error => {
          this.errors = ["Invalid email or password."];
          this.email = "";
          this.password = "";
        });
    }
  }
};
</script>