<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <article v-for="post in posts" :key="post.id" v-on:click="edit(post.id)" title="leer mas">
      <h1>{{post.title}}</h1>
      <p>{{post.body}}</p>
    </article>
  </div>
</template>

<script>

import axios  from "axios";

export default {
  name: 'Posts',
  props: {
    msg: String
  },
  data(){
    return {
      posts: []
    }
  },
  mounted() {
    axios.get("https://jsonplaceholder.typicode.com/posts")
    .then(data => {
      this.posts = data.data;
    }) 
  },
  methods: {
    edit(id){
      this.$router.push("/post/" + id);
    }
  }


}



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  article {
    cursor: pointer;
  }

  article:hover {
    background-color: #eee;
  }
</style>
