<template>
  <div class="PostIndex">
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
      message: "This is the post index!",
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
