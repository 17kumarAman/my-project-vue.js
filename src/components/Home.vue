<template>
    <Header />
<h1>Hello {{ name }}, Welcome On Home Page </h1>
<table border="'1'">
    <tr>
    <td>Id</td>
    <td>Name</td>
    <td>Address</td>
    <td>Contact</td>
</tr>
    <tr v-for="items in resturants" :key="items.id">
        <td>{{ items.id }}</td>
        <td>{{ items.name }}</td>
        <td>{{ items.address }}</td>
        <td>{{ items.contact }}</td>

    </tr>
</table>
</template>

<script setup>import axios from 'axios';
import Header from './Header.vue'
import { onMounted , reactive, ref} from 'vue';
import router from '/src/router.js';

let name = ref('');
let resturants = ref([])
 onMounted(async()=>{
    let user = localStorage.getItem('user-info')
    name.value = JSON.parse(user).nameid
    // console.log(name)
    if(!user){
        router.push({name:'SignUp'})
    }
    let res = await axios.get("http://localhost:3000/resturant");
    console.log(res)
    resturants.value = res.data
})
console.log(name.value)
</script>

<style>
    td{
        width:160px;
        height: 40px;
    }
</style>