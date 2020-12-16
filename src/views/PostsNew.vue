<template>
  <div class="posts-new">
    <form v-on:submit.prevent="submit()">
    <h1>Make a new post</h1>
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
