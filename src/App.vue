<template>
  <div id="app">
    <postForm />
    <h1>{{postsCount}}</h1>
    <div class="post" v-for="post in validPosts" :key="post.id">
      <h2>{{post.title}}</h2>
      <p>{{post.body}}</p>
    </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
import postForm from './components/postForm.vue'
export default {
  name: 'app',
  components: {postForm},
  computed: mapGetters(['validPosts', 'postsCount']),
  methods: mapActions(['fetchPosts']),
  async mounted() {
    this.fetchPosts(4)
  }
}
</script>

<style>
#app {
  margin: 60px auto;
  width: 400px;
}
.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 10px;
  text-align: center;
}
</style>
