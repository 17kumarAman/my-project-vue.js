<template>
    <Header />
<h1>Hello users Welcome On Update Resturants Page </h1>
</template>

<script setup>
import Header from './Header.vue'
import { onMounted } from 'vue';
import router from '/src/router.js';
onMounted(()=>{
    let user = localStorage.getItem('user-info')
    if(!user){
        router.push({name:'SignUp'})
    }
})
</script>