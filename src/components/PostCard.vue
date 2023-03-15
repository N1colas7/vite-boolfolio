<script>
export default {
    name:'PostCard',
    props:{
        post:Object,
        baseUrl:String
    }
}
</script>
<template lang="">
    <div>
        <div class="card my-3">
            <div class="card-img-top">
                <img class="img-fluid" :src="post.cover_image !=null ? `${baseUrl}/storage/${post.cover_image}` : 'https://picsum.photos/300/200'" >
            </div>
            <div class="card-title">
                <h5>{{ post.title }}</h5>
                <em>Tecnologia: {{ post.technologies.name }}</em>
                <!-- <em>Type: {{ post.type.slug }}</em> -->
            </div>
            <div class="card-text">
                {{ post.content }}
            </div>
            <a href="#" class="btn btn-sm btn-success">
                Leggi il post
            </a>
        </div>
    </div>
</template>
<style lang="">
    
</style>