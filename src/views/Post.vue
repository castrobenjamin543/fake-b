<template>
  <div class="hello">
    <div>
      <h1>{{title}}</h1>
      <p>{{body}}</p>
    </div>
    <h2>comments</h2>
    <section class="comments">
      <div v-for="comment in comments" :key="comment">
        <h5>{{comment.name}}</h5>
        <span>{{comment.email}}</span>
        <p>{{comment.body}}</p>
      </div>
    </section>
  </div>
</template>

<script>

import axios  from "axios";

export default {
  name: 'Post',
  data(){
    return {
      id: null,
      title: "",
      body: "",
      comments: []
    }
  },
  mounted() {
    this.id = this.$route.params.id;

    axios.get("https://jsonplaceholder.typicode.com/posts/"  + this.id)
    .then(data => {
      this.title = data.data.title;
      this.body = data.data.body;
    })
    axios.get("https://jsonplaceholder.typicode.com/comments?postId="  + this.id)
    .then(data => {
      this.comments = data.data;
    }) 
  } 
}


</script>
