<script>
export default {
    name: "PostMain",
    data() {
        return {
            posts: [],
            loading: true,
            baseUrl: 'http:/127.0.0.1:8000'
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
    <div>
        <button class="btn btn-primary">ciao</button>
    </div>
</template>
<style lang="scss" scoped>

</style>