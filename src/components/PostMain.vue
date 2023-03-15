<script>
import axios from 'axios';

export default {
    name: "PostMain",
    data() {
        return {
            posts: [],
            loading: true,
            baseUrl: 'http://127.0.0.1:8000',
            currentPage: 1,
            lastPage: null
        }
    },
    methods: {
        getPosts(post_page) {
            this.loading = true;
            axios.get(`${this.baseUrl}/api/posts`, { params: { page: post_page} }).then((response) => {
                if (response.data.success) {

                    this.posts = response.data.posts;
                    this.currentPage = response.data.posts.current_page;
                    this.lastPage = response.data.posts.last_page;
                    this.loading = false;
                }
                else {
                    //compare messaggio che non è andata a buon fine la chiamata

                }
            });
        }
    },
    mounted() {
        this.getPosts(this.currentPage)
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
                    <div class="card my-3" v-for="post in posts" :key="post_id">
                        <div class="card-img-top">
                            <!-- <img class="img-fluid" :src="post.cover_image !=null ? `${baseUrl}/${post.cover_image}` : 'https://picsum.photos/200/300'" > -->
                        </div>
                        <div class="card-title">
                            <h5>{{ posts.title }}</h5>
                        </div>
                        <div class="card-text">
                            {{ posts.content }}
                        </div>
                        <a href="#" class="btn btn-sm btn-success">
                            Leggi il post
                        </a>
                    </div>
                    <div class="row">
                        <div class="col-12">
                            <nav>
                                <ul class="pagination">
                                    <li :class="currentPage === 1 ? 'disabled' : 'page-item'">
                                        <button class="page-link" @click="getPosts(currentPage - 1)">Prev</button>
                                    </li>
                                    <li  class="page-item" v-for="i in [1,lastPage]">
                                        <button class="page-link" @click="getPosts(i)">
                                            {{ i }}
                                        </button>
                                    </li>
                                    <li :class="currentPage === lastPage ? 'disabled' : 'page-item'">
                                        <button class="page-link" @click="getPosts(currentPage + 1)">Next</button>
                                    </li>
                                </ul>
                            </nav>
                        </div>
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