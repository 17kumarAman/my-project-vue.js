<template>
    <Header />
<h1>Hello users, Welcome On Add Resturant Page </h1>
<form class="login" >
    <input type="text" name="name" v-model="name" placeholder="Enter Name">
    <input type="text" name="address" v-model="address" placeholder="Enter Address">
    <input type="text" name="contact" v-model="contact" placeholder="Enter Contact">
    <button type="button" @click="addResturant">Add New Resturant</button>
</form>
</template>

<script setup>
import Header from './Header.vue'
import { onMounted } from 'vue';
import router from '/src/router.js';
import { ref } from 'vue';
import axios from 'axios';

let name = ref('')
let address = ref('')
let contact = ref('')

async function addResturant(){
    console.log('SignUp' , name.value , email.value , password.value)
    let res = await axios.post('http://localhost:3000/resturant',{
        name:name.value,
        address:address.value,
        contact :contact.value
    })
    console.log(res.data)
    if(res.status==201){
        router.push({name:'Home'})
    }

}

onMounted(()=>{
    let user = localStorage.getItem('user-info')
    if(!user){
        router.push({name:'SignUp'})
    }
})
</script>

<style>
.heading{
    padding-left: 25px;
}
.img{
    padding-right: auto;
    height: 100px;
}
.logo{margin-top: 50px;
    width: 100px;
    margin-bottom: 30px;
    padding-right: 30px;
    margin-left: auto;
    margin-right: auto;
    /* background-color: blue; */
    
}
.login input{
    
    width: 320px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid skyblue;

}
.login button{
    width: 350px;
    height: 43px;
    border: 1px solid skyblue;
    cursor: pointer;
    color: #fff;
    background-color: skyblue;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
}
p{
    width: 350px;
    height: 43px;
   
    cursor: pointer;
    color: #fff;
    padding-right: auto;
    padding-left:310px;
    /* display: block; */
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto; 
    
}
body{
    background-color: rgb(249, 246, 246);
}
</style>