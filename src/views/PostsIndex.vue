<template>
  <div class="posts-index">
    <h1>{{ message }}</h1>
    <!-- <h1>{{ posts }}</h1> -->
    <div v-for="post in filterBy(posts, searchTerm, 'title')">
      <p>{{ post.title }}</p>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
import Vue2Filters from "vue2-filters";
export default {
  mixins: [Vue2Filters.mixin],
  data: function () {
    return {
      message: "This is the post index!",
      posts: [],
      searchTerm: "",
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
