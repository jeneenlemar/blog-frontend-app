<template>
  <div class="posts-show">
    <h1>{{ message }}</h1>

  

    <div>
      <h2>Title: {{ post.title }}</h2>
      <h2>Body: {{ post.body }}</h2>
      <!-- <h2>Image: {{ post.image }}</h2> -->
      <img v-bind:src="post.image" alt=""><br>
    </div>
    User that posted: {{ post.user_id }}<br>
    Current User: {{ $parent.getUserId()}} <br>


    <router-link v-if="post.user_id == $parent.getUserId()" :to="`/posts/${post.id}/edit`">Edit</router-link>

    <!-- note : to test the item I replaced the $parent.getUserId() with a 1 because this data was made with users made before me and with passwords I didn't have to test.... I did work, then I changed it back.  I know we could change the info in the forms and data if we wanted, but I didn't take it that far -->

  </div>
</template>

<style>
 img {
  width: 250px;
 }
</style>

<script>
// var axios = require("axios");
import axios from 'axios';
export default {
  data: function() {
    return {
      message: "Blog Post Show",
      post: {},
    };
  },
  // respone = HTTP.get("/api/recipes")
  // @recipes = response.parse
  created: function() {
    axios.get(`/api/posts/${this.$route.params.id}`).then(response => {
      console.log(response.data);
      this.post = response.data;
    });
  },
  methods: {}
    
};
</script>