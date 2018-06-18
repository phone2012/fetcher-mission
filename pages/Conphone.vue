<template lang="html">
  <div class="container">
    <div class="topic">
        <strong>-  SHOW  DATA  -</strong>
    </div>
    <div class="display">
      <div class="txt">
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
.container{
  display           : flex;
  flex-direction    : column;
}
.topic{
   display           : flex;
  flex-direction    : column;
  font-size          : 2.25rem;
  background-color   :#3d0099;
  width              : 80%;
  height             : 200px;
  margin-left        : 150px;

}
.display{
  width              : 80%;
  height             : 1500px;
  color              : black;
  font-size          : 2.25rem;
  margin-left        : 150px;
  background-color   :#9966ff;
}
.txt{
width              : 70%;
height             : 1500px;
color              : black;
font-size          : 2.25rem;
margin             : 150px;
background-color   :#9966ff;

}

</style>
