<template>

  <div class="posts-new">
    <form v-on:submit.prevent="submit()">
      <h1>Make a new post</h1>
      <ul>
        <li class="text-danger" v-for="error in errors">{{ error }}</li>
      </ul>
      <div class="form-group">
        <label>Title:</label> 
        <input type="text" class="form-control" v-model="title">
      </div>
      <!-- <div class="form-group">
        <label>Ingredients:</label>
        <input type="text" class="form-control" v-model="ingredients">
      </div>
      <div class="form-group">
        <label>Directions:</label>
        <input type="text" class="form-control" v-model="directions">
      </div>
      <div class="form-group">
        <label>Prep Time:</label>
        <input type="text" class="form-control" v-model="prepTime">
      </div>
      <div class="form-group">
        <label>Image Url:</label>
        <input type="text" class="form-control" v-model="imageUrl">
      </div> -->
      <input type="submit" class="btn btn-primary" value="Submit">
    </form>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "This is the post index!",
      posts: [],
    };
  },
  created: function () {
    this.postsIndex();
  },
  methods: {
    postsIndex: function () {
      console.log("in posts index");
      axios.get("/api/posts").then((response) => {
        console.log(response.data);
        this.posts = response.post;
      });
    },
  },
};
</script>
