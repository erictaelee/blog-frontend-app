<template>
  <div class="recipes-show">
    <h1>{{ message }}</h1>
    <p><b>id:</b> {{ post.id }}</p>
    <p><b>title:</b> {{ post.title }}</p>
    <p><b>image:</b> {{ post.image }}</p>
    <p><b>body:</b> {{ post.body }}</p>

    <!-- <img v-bind:src="post.image">
    <br />
    <p>post.user_id: {{ post.user_id }}</p>
    <p>$parent.getUserId(): {{ $parent.getUserId() }}</p>
    <div v-if="post.user_id == $parent.getUserId()">
      <router-link v-bind:to="`/posts/${this.$route.params.id}/edit`">Edit post</router-link>
      <br />
      <button v-on:click="deletePost()">Delete the post</button> -->
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
      message: "Welcome to the show!",
      post: {},
    };
  },
  created: function () {
    // get data about an individual post from rails
    // params[:id]
    console.log(this.$route.params.id);
    // axios.get("/api/posts/" + this.$route.params.id).then(response => {
    axios.get(`/api/posts/${this.$route.params.id}`).then((response) => {
      console.log(response.data);
      this.post = response.data;
    });
  },
  methods: {
    deletePost: function () {
      console.log("deleting post...");
      axios.delete(`/api/posts/${this.$route.params.id}`).then((response) => {
        console.log(response.data);
        this.$router.push("/posts");
      });
    },
  },
};
// show the image
// link from this page to the index page
// link from the index page to this page
// route is bad
</script>