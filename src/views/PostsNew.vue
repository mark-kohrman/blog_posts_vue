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
      <div class="form-group">
        <label>Body:</label>
        <input type="text" class="form-control" v-model="body">
        <small v-if="body.length <= 100">You have {{ 100 - body.length }} chararcters remaining"</small>
      </div>
      <div class="form-group">
        <label>Image:</label>
        <input type="text" class="form-control" v-model="image">
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
      console.log(params);
      axios.post("api/posts", params).then((response) => {
        this.$router.push("/posts");
      });
    },
  },
};
</script>