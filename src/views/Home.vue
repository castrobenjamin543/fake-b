<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <Posts msg="Obteniendo articulo:"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Posts from '@/components/Posts.vue'

export default {
  name: 'Home',
  components: {
    Posts
  }
}
</script>
