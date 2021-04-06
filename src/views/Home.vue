<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h1>{{ posts }}</h1>

  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      posts: [],
    };
  },
  created: function () {
    this.postsIndex();
  },
  methods: {
    postsIndex: function () {
      console.log("in posts index...");
      axios.get("http://localhost:3000/api/posts").then((response) => {
        console.log(response.data);
        this.posts = response.data;
      });
    },
  },
};
</script>