<template>

  <div class="posts-edit">
    <form v-on:submit.prevent="submit()">
      <h1>Edit a post</h1>
      <ul>
        <li class="text-danger" v-for="error in errors">{{ error }}</li>
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
        <input type="text" class="form-control" v-model="Image">
      </div>
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
      body: "",
      image: "",
      posts: [],
    };
  },
  created: function () {
    console.log("in created...");
    this.postsIndex();
  },
  methods: {
    submit: function () {
      var params = {
        title: this.title,
        body: this.body,
        image: this.image,
      };
      axios
        .patch("/api/posts/" + this.$route.params.id, params)
        .then((response) => {
          this.$router.push("/posts/" + this.$route.params.id);
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
    getPostData: function () {
      // get data to prepopulate the form
      axios.get("/api/postss/" + this.$route.params.id).then((response) => {
        console.log(response.data);
        this.title = response.data.title;
        this.body = response.data.body;
        this.image = response.data.image;
      });
    },
  },
};
</script>
