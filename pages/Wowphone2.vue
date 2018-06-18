<template>
  <div class="container">
  <wowdat   v-show="appear" :count="num"></wowdat>
  <wowerr   v-show="appear1" :count1="num1"></wowerr>
    <div class="topic">
      <strong>-  SHOW MY DATA  -</strong>

    </div>
    <div class="display">
      <div class="display1">
        <button @click="warn('Form cannot be submitted yet.', $event)">
          show data
        </button>
        <button @click="warn2('Form cannot be submitted yet.', $event)">
          show data error
        </button>
      </div>
      <ul v-if="posts && posts.length">
        <li
          v-for="post of posts"
          :key="post.name">
          <p>{{ post.id }}</p>
          <p><strong>{{ post.name }}</strong></p>
          <p>{{ post.email }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import wowdat from '@/components/wowdat'
import wowerr from '@/components/wowerr'

export default {
  components: {
    wowdat,
    wowerr,

  },
  data() {
    return {
      posts: [],
      errors: [],
      num: '',
      num1: '',
      appear: false,
      appear1: false,
    };
  },
  methods: {
    warn(message, event) {
      if (event) event.preventDefault();
      axios.get('https://jsonplaceholder.typicode.com/users')
        .then((response) => {
          this.posts = response.data;
          console.log(this.posts);
          // alert('get 10 data');
          this.num = this.posts.length+"Data Addes";
          this.appear = true;
        })
        .catch((e) => {
          this.errors.push(e);
        });
    },
    warn2(message, event) {
      this.posts = [];
      this.appear = false;
      if (event) event.preventDefault();
      axios.get('https://reqres.in/api/unknown/23')
        .then((response) => {
          this.posts = response.data;
          console.log(this.posts);
          this.num1 = this.errors.length+"Data Addes";
          this.appear1 = true;
        })
        .catch((e) => {
          this.errors.push(e);
          this.num1 = e+"";
          this.appear1 = true;
        });
    },
  },
};
</script>
<style lang="css">
  body{
      margin            : 0;
      padding           : 0;
  }
  .container {
    display           : flex;
    flex-direction    : column;
    width             : 100%;
    height            : 1800px;
    background-color  : #d9d9d9;
  }
  .display {
    display           : flex;
    flex-direction    : column;
    width             : 95%;
    height            : 95%;
    margin-left       : 55px;
    background-color  : #ccccff;
  }
  .display1 {
    display           : flex;
    flex-direction    : column;
    width             : 10%;
    height            : 5%;
    margin-top        : 30px;
    background-color  : #ccccff;
  }
  .topic {
    display           : flex;
    flex-direction    : column;
    width             : 100%;
    height            : 5%;
    background-color  : black;
    color             : white;
    font-size         : 6em;
  }

</style>
