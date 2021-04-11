
<template>
  <div class="signup">
    <!-- chef
    ingredients
    directions 
    prep_time
    image_url
    title -->
    
    
    <form v-on:submit.prevent="submit()">
      <h1>Make a new Post</h1>
      <ul>
        <li class="text-danger" v-for="error in errors" v-bind:key="error">
          {{ error }}
        </li>
      </ul>
      <div class="form-group">
        <label>Title:</label>
        <input type="text" class="form-control" v-model="title">
      </div>
      <div class="form-group">
        <label>Body:</label> 
        <input type="text" class="form-control" v-model="body">
      </div>
      <div class="form-group">
        <label>Image:</label>
        <input type="text" class="form-control" v-model="image">
      </div>
   
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      title: "",
      body: "",
      image: "",
      errors: [],
    };
  },
  methods: {
    submit: function () {
      var params = {
        title: this.title,
        body: this.body,
        image: this.image,
      };
      axios
        .post("/api/posts", params)
        .then((response) => {
          console.log(response.data);
          this.$router.push("/posts");
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>