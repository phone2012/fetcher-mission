<template lang="html">
  <div class="container">
  <!-- <p>Math.floor(Math.random() * 100) + 1) returns a random integer between 1 and 100 (both included).</p> -->
    <div class="display">
      <h2>JavaScript Math</h2>
      <button @click="myFunction()">GetData</button>
      <p>{{ num }}</p>
      <p>{{ posts.title }}</p>
      <ul>
        <li
          v-for="post1 of posts1"
          :key="post1.id">
          <p>{{ post1.body }}</p>
          <p>{{ post1.email }}</p>
        </li>
      </ul>
   </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      posts: [],
      posts1: [],
      errors: [],
      num: 0,

    };
  },
  methods: {
    myFunction() {
       this.num = Math.floor((Math.random() * 100) + 1);
       axios.get('https://jsonplaceholder.typicode.com/posts/' + this.num)
       .then((response) => {
           this.posts = response.data;
           console.log(this.posts);
           })
       axios.get('https://jsonplaceholder.typicode.com/posts/' + this.num + '/comments')
       .then((response) => {
       this.posts1 = response.data;
       console.log(this.posts1);
               })
   },

 },
};
</script>

<style lang="css">
.display{
  width              : 90%;
  height             : 1500px;
  color              : black;
  font-size          : 2.25rem;
  margin             : 50px;
  background-color   :lightgray;
}

</style>
