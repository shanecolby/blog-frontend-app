<template>

  <div class="posts-new">
    <form v-on:submit.prevent="submit()">
       <!-- <img v-if="status" v-bind:src="`https://http.cat/${status}`" width="700px"> -->

      <h1>Make a new post</h1>
      <ul>
        <li class="text-danger" v-for="error in errors"{{ error }}</li>
      </ul>
      <div class="form-group">
        <label>Title:</label> 
        <input type="text" class="form-control" v-model="title">

      </div>
      <div class="form-group">
        <label>New Post:</label>
        <input type="text" class="form-control" v-model="posts">
      </div>
      <!-- <div class="form-group">
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
      title: "",
      posts: [],
    };
  },
  created: function () {
    this.postsIndex();
  },
  methods: {
    submit: function () {
      var params = {
        title: this.title,
        post: this.post,
      };
      axios
        .post("/api/posts", params)
        .then((repsonse) => {
          this.$router.push("/posts");
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
    // postIndex: function () {
    //   console.log("in posts index");
    //   axios.get("/api/posts").then((response) => {
    //     console.log(response.data);
    //     this.posts = response.post;
    //   });
    // },
  },
};
</script>
