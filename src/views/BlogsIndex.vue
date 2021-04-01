  
<template>
  <div class="blogs-index">
    <!-- recipes.each do |recipe| -->
    <div v-for="blog in blogs">
      {{ blog.title }}
      <hr >
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Recipes index page",
      blogs: [],
    };
  },
  created: function () {
    this.blogsIndex();
  },
  methods: {
    blogsIndex: function () {
      console.log("on the index paage...");
      // make a web request to rails to get all the recipes
      axios.get("/api/blogs").then((response) => {
        console.log(response.data);
        this.blogs = response.data;
      });
    },
  },
};
</script>