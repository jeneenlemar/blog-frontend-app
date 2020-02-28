<template>
  <div class="posts-index">

    <!-- added boostrap -->

 <!--    <div class="card-deck">
  <div class="card">
    <img src="..." class="card-img-top" alt="...">
    <div class="card-body">
      <h5 class="card-title">Card title</h5>
      <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>
      <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
    </div>
  </div>
  <div class="card">
    <img src="..." class="card-img-top" alt="...">
    <div class="card-body">
      <h5 class="card-title">Card title</h5>
      <p class="card-text">This card has supporting text below as a natural lead-in to additional content.</p>
      <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
    </div>
  </div>
  <div class="card">
    <img src="..." class="card-img-top" alt="...">
    <div class="card-body">
      <h5 class="card-title">Card title</h5>
      <p class="card-text">This is a wider card with supporting text below as a natural lead-in to additional content. This card has even longer content than the first to show that equal height action.</p>
      <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
    </div>
  </div>
</div> -->

<!-- end of added bootstrap -->

<!-- single card bootstrap -->
<!-- <div class="card" style="width: 18rem;">
  <img src="..." class="card-img-top" alt="...">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
 -->


<!-- end of single card bootstrap -->


    <h1>{{ message }}</h1>

    <div> 
      <div v-for="post in posts" v-on:click="currentPost = post" v-bind:class="{ selected: post === currentPost }">
        <h2>Title: {{ post.title }}</h2>
        <router-link :to="`/posts/${post.id}`">
          <img v-bind:src="post.image" alt=""><br>
        </router-link>
      </div>
    </div>
  </div>
</template>

<style>
  div {
    padding-bottom: 8px;
  }
 img {
  width: 250px;
 }
 .selected {
  color: white;
  background-color: blue;
  border: solid black 5px;
  padding: 2px;


 }
</style>

<script>
// var axios = require("axios");
import axios from 'axios';
export default {
  data: function() {
    return {
      message: "Blog Post Frontend",
      posts: [],
      currentPost: {}
    };
  },
  // respone = HTTP.get("/api/recipes")
  // @recipes = response.parse
  created: function() {
    axios.get("/api/posts").then(response => {
      response.data.forEach(post => {
        post.showExtraInfo = false;
      });
      console.log(response.data);
      this.posts = response.data;
    });
  },
  methods: {}
    
};
</script>