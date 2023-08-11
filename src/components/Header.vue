<template>  
    
    <div class="nav">
        <router-link to="/">Home</router-link>router-link
        <router-link to="add">Add Resturant</router-link>
        <router-link to="update">Update Resturant</router-link>
        <a @click="logOut" href="#">Logout</a>
    </div>
</template>

<script setup>
import router from '/src/router.js';

    function logOut(){
    localStorage.clear();
    router.push({name:'Login'})
}
</script>


<style>
.nav{
    background-color: #333;
    overflow: hidden;
}
.nav a{
    color: #f2f2f2;
    float:left;
    text-align: center;
    padding: 10px 14px;
    text-decoration: none;
    font-size: 16px;
    margin-right: 4px 5px;
}
.nav a:hover{
    background-color: #ddd;
    color:#222
}
</style>