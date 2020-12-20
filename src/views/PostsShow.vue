<template>
  <div class="posts-show">
    <h1>{{ message }}</h1>
    <h1>title: {{ post.title }}</h1>
    <h1>body: {{ post.body }}</h1>
    <h1>image: {{ post.image }}</h1>
<!-- 
    <router-link v-bind:to="`/recipes/${recipe.id}/edit`">Edit</router-link> -->
    <h1>User id? {{$parent.getUserId()}}</h1>
    <h1>Get Id of the post {{post.user_id}}</h1>
    <router-link v-if="$parent.getUserId() == post.user_id" v-bind:to="`/posts/${post.id}/edit`"</router-link>
    <br>

    <!-- <button v-on:click="postsDestroy()">Delete</button> -->
    <button v-if="$parent.getUserId() == post.user_id" v-on:click="postsDestroy()">Delete</button>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to the show",
      post: {},
    };
  },
  created: function () {
    this.postsShow();
  },
  methods: {
    postsShow: function () {
      console.log("in post show");
      axios.get("/api/posts/3").then((response) => {
        console.log(response.data);
        this.post = response.data;
      });
    },
    // postsDestroy: function () {
    //   console.log("destroying post..."),
    //     axios.delete("/api/posts/${this.post.id}").then((response) => {
    //       console.log(response.data);
    //       this.$router.push("/posts");
    //     });
    // },
  },
};
</script>