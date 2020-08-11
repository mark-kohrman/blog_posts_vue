<template>
  <div class="posts-new">
    <form v-on:submit.prevent="submit()">
    <h1>Edit a currently existing post</h1>
    {{  post  }}
     <ul>
        <li class="text-danger" v-for="error in errors">{{ error }}</li>
      </ul>
      <div class="form-group">
        <label>Title:</label> 
        <input type="text" class="form-control" v-model="post.title">
      </div>
      <div class="form-group">
        <label>Body:</label>
        <input type="text" class="form-control" v-model="post.body">
      </div>
      <div class="form-group">
        <label>Image:</label>
        <input type="text" class="form-control" v-model="post.image">
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
      post: {},
      errors: [],
    };
  },
  created: function () {},
  methods: {
    submit: function () {
      var params = {
        title: this.post.title,
        body: this.post.body,
        image: this.post.image,
      };
      console.log(params);
    },
    showPost: function () {
      console.log("showing the post");
      console.log(this.$route);
      axios.get(`/api/posts/${this.$route.params.id}`).then((response) => {
        console.log(response.data);
        this.post = response.data;
      });
    },
  },
};
</script>