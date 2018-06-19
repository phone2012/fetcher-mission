<template lang="html">
  <div class="container">
    <div class="topic">
      <div class="totxt">
        <strong><font face="Comic Sans MS">-  SHOW  DATA  -</font></strong>
      </div>
    </div>
    <div class="display">
      <div class="txt">
       <button @click="myFunction()">GetData</button>
       <br /><strong>{{ num }}</strong><br />
         <strong><font face="Trebuchet MS">{{ posts.title }}</font></strong><br />
       <ul>
         <li
           v-for="post1 of posts1"
           :key="post1.id">
           <div class="txtt">
           <p><font face="Lucida Console">{{ post1.body }}</font></p>
          <p><font face="Lucida Console">{{ post1.email }}</font></p>
          </div>
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
  width              : 100%;

}
.topic{
   display           : flex;
  flex-direction    : column;

  background-color   :#1a1aff;
  width              : 90%;
  height             : 200px;
  margin-left        : 100px;

}
.display{
  width              : 90%;
  height             : 1600px;
  color              : black;
  font-size          : 2.25rem;
  margin-left        : 100px;
  background-color   :#6666ff;
}
.txt{
width              : 70%;
height             : 1000px;
color              : black;
font-size          : 2.25rem;
margin-left        : 150px;
}
.totxt{
  font-size          : 3.25rem;
  margin             : 70px;
}
.txtt{
  margin             : 15px;
  border             : 5px solid #999999;
  background-color   :#8080ff;
}
@media only screen and (min-width:768px) and (max-width:1024px){
.container{
    display           : flex;
    flex-direction    : column;
  }
.topic{
     display           : flex;
    flex-direction    : column;

    background-color   :#3333cc;
    width              : 90%;
    height             : 200px;
    margin-left        : 50px;

  }
.display{
    width              : 90%;
    height             : 1500px;
    color              : black;
    font-size          : 2.25rem;
    margin-left        : 50px;
    background-color   :#4747d1;
  }
.txt{
  width              : 80%;
  height             : 1000px;
  color              : black;
  font-size          : 2.25rem;
  margin-left        : 50px;
  background-color   :#4747d1;

  }
.totxt{
    font-size          : 3.25rem;
    margin             : 70px;
 }
 .txtt{
   margin             : 15px;
   border             : 5px solid #999999;
   background-color   :#8080ff;
 }
}

  @media only screen and (max-width:767px) {
    .container{
      display           : flex;
      flex-direction    : column;
      width             : 100%;
      margin-left       : 0;
}
.topic{
       display           : flex;
      flex-direction    : column;

      background-color   :#3d0099;
      width              : 95%;
      height             : 150px;
      margin-left        : 10px;

    }
.display{
      width              : 95%;
      max-height         : 100%;
      color              : black;
      font-size          : 2.25rem;
      margin-left        : 10px;
      background-color   :#9966ff;
    }
.txt{
    width              : 80%;
    max-height         : 100%;
    color              : black;
    font-size          : 1.25rem;
    margin-left        : 20px;
    background-color   :#9966ff;

   }
.totxt{
      font-size          : 2.25rem;
      margin             : 20px;
      margin-top         : 50px;
  }
}
@media only screen and (max-width:320px) {
  .container{
    display           : flex;
    flex-direction    : column;
    width             : 100%;
    margin-left       : 0;
}
.topic{
     display           : flex;
    flex-direction    : column;

    background-color   :#3d0099;
    width              : 95%;
    height             : 150px;
    margin-left        : 10px;

  }
.display{
    width              : 95%;
    max-height         : 100%;
    color              : black;
    font-size          : 2.25rem;
    margin-left        : 10px;
    background-color   :#9966ff;
  }
.txt{
  width              : 80%;
  max-height         : 100%;
  color              : black;
  font-size          : 1.00rem;
  margin-left        : 20px;
  background-color   :#9966ff;

 }
.totxt{
    font-size          : 2.25rem;
    margin             : 20px;
    margin-top         : 50px;
 }
 .txtt{
   margin             : 15px;
   border             : 5px solid #999999;
   background-color   :#8080ff;
 }
}
@media only screen and (max-width:270px) {
  .container{
    display           : flex;
    flex-direction    : column;
    width             : 100%;
    margin-left       : 0;
}
.topic{
     display           : flex;
    flex-direction    : column;

    background-color   :#3d0099;
    width              : 99%;
    height             : 90px;
    margin-left        : 5px;

  }
.display{
    width              : 99%;
    max-height         : 100%;
    color              : black;
    font-size          : 2.25rem;
    margin-left        : 5px;
    background-color   :#9966ff;
  }
.txt{
  width              : 80%;
  max-height         : 100%;
  color              : black;
  font-size          : 0.90rem;
  margin-left        : 20px;
  background-color   :#9966ff;

 }
.totxt{
    font-size          : 1.55rem;
    margin             : 20px;
    margin-top         : 20px;
 }
}
</style>
