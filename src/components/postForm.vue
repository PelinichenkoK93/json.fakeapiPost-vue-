<template>
    <form @submit.prevent="submit">
        <input type="text" v-model="title" placeholder="title">
        <input type="text" v-model="body" placeholder="body">
        <button type="submit">Create</button>
    </form>
</template>

<script>
import {mapMutations} from 'vuex'
export default {
    data() {
        return {
            title: '',
            body: ''
        }
    },
    methods: {
        ...mapMutations(['createPost']),
       submit() {
          this.createPost({
              title: this.title,
              body: this.body,
              id: Date.now()
          })
          this.title = this.body == ""
       } 
    }
}
</script>

<style>
input {
    display: block;
    width: 100%;
    border: 1px solid #ccc;
    border-radius: 2px;
    padding: 10px;
    margin-bottom: 10px;
}
</style>