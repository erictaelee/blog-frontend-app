<template>
  <div class="home">
    <h1>{{ message }}</h1>

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
    };
  },
  created: function () {
    this.posts.Index();
  },
  methods: {
    postsIndex: function () {
      console.log("on the index page......");
    },
  },
};
</script>