<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h1>title: {{  post.title  }}</h1>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to showww!",
      post: {},
    };
  },
  created: function () {
    this.showPost();
  },
  methods: {
    showPost: function () {
      console.log("show the post!!!!");
      console.log(this.$route.params.id);

      axios.get;
    },
  },
};
</script>