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
            currentPage: 1,
            lastPage: null,
            loading: false
        }
    },
    methods: {
        getPosts(postPage = 1){
            axios.get(`http://127.0.0.1:8000/api/posts?page=${postPage}`)
            .then((response) => {
                console.log(response.data.results.data);
                this.posts = response.data.results.data;
                // this.currentPage = response.data.
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