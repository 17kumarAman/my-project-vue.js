<template>
    <div class="logo">
        <img class="img" src="../assets/res.png" >
    <h2 class="heading">Sign Up</h2>
    </div>
    
<div class="register">
    
    <input type="text" v-model="name" placeholder="Enter Name">
    <input type="text" v-model="email" placeholder="Enter Email">
    <input type="password" v-model="password" placeholder="Enter Password">
    <button @click="signUp">Sign Up</button>
</div>

</template>

<script setup>
import {onMounted, ref} from 'vue'
import axios from 'axios'
import router from '/src/router.js';
const name = ref('');
const email = ref('');
const password = ref('');
async function signUp(){
    console.log('SignUp' , name.value , email.value , password.value)
    let res = await axios.post('http://localhost:3000/user',{
        email:email.value,
        name:name.value,
        password :password.value
    })
    console.log(res.data)
    if(res.status==201){
        localStorage.setItem("user-info",JSON.stringify(res.data))
        router.push({name:'Home'})
    }

}
onMounted(()=>{
    let user = localStorage.getItem('user-info')
    if(user){
        router.push({name:'Home'})
    }
})

</script>


<style>
.heading{
    padding-left: 15px;
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
.register input{
    
    width: 320px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid skyblue;

}
.register button{
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
body{
    background-color: rgb(249, 246, 246);
}
</style>