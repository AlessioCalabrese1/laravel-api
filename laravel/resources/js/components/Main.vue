<template>
  <section>
    Sono nel main
    <ul>
        <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
    </ul>
  </section>
</template>

<script>
import axios from 'axios';
export default {
    data: function(){
        return{
            posts: [],
        }
    },
    methods: {
        getPosts(){
            axios.get('http://127.0.0.1:8000/api/posts')
            .then((response) => {
                console.log(response.data.results);
                this.posts = response.data.results;
            }).catch((error) => {
                console.error(error);
            })
        }
    },

    created(){
        this.getPosts();
    }
}
</script>

<style>

</style>