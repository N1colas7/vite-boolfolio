<script>
import axios from 'axios';

export default {
    name: "PostMain",
    data() {
        return {
            posts: [],
            loading: true,
            baseUrl: 'http://127.0.0.1:8000'
        }
    },
    methods: {
        getPosts() {
            this.loading = true;
            axios.get(`${this.baseUrl}/api/posts`).then((response) => {
                if (response.data.success) {
                    this.posts = response.data.posts
                    this.loading = false;
                }
                else {
                    //compare messaggio che non è andata a buon fine la chiamata

                }
            });
        }
    },
    mounted() {
        this.getPosts()
    },
}
</script>
<template lang="">
    <div class="container">
        <div class="row">
            <div class="col-12 text-center">
                <h1>Boolpress</h1>
            </div>
            <div class="col-12" >
                <div v-if="loading" class="d-flex justify-content-center">
                    <div class="loader"></div>
                </div>
                <div v-else class="d-flex justify-content-center flex-wrap m-5">
                    <div class="card my-3" v-for="post in posts" :key="post.id">
                        <div class="card-img-top">
                            <img class="img-fluid" :src="post.cover_image !=null ? `${baseUrl}/${post.cover_image}` : 'https://picsum.photos/200/300'" >
                        </div>
                        <div class="card-title">
                            <h5>{{ post.title }}</h5>
                        </div>
                        <div class="card-text">
                            {{ post.content }}
                        </div>
                        <a href="#" class="btn btn-sm btn-success">
                            Leggi il post
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
    .loader {
    border: 16px solid #f3f3f3; /* Light grey */
    border-top: 16px solid #3498db; /* Blue */
    border-radius: 50%;
    width: 120px;
    height: 120px;
    animation: spin 2s linear infinite;
    }

    @keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
    }
</style>