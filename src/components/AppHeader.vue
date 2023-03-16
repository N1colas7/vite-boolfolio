<script>
export default {
    name:'AppHeader',
    data() {
        return {
            menuItems : [
                {
                    label: 'HomePage',
                    routeName: 'homepage',
                    //link: '/'
                },
                {
                    label: 'Blog',
                    routeName: 'post_list'
                },
                {
                    label:'Contatti',
                    routeName: 'contacts'
                }
            ]
        }
    },
}
</script>
<template lang="">
    <nav class="navbar navbar-expand-md background-nav">
        <div class="container">
            <div class="navbar-brand">
                <img src="/img/prova.jpeg" class="img-fluid" alt="photo">
            </div>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item" v-for="(item, index) in menuItems" :key="index">
                        <!-- <a :href="item.link" class="nav-link text-white">
                            {{ item.label }}
                        </a> -->
                        <router-link :to="{ name: item.routeName }" class="nav-link">
                            {{ item.label }}
                        </router-link>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>
<style lang="scss" scoped>
    .background-nav{
        background-color: rgb(255, 127, 127);
    }
</style>