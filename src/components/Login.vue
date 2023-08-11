<template>
    <div class="logo">
        <img class="img" src="../assets/res.png" >
        <h1 class="heading">Login</h1>
    </div>
<div class="login">
    
    <input type="text" v-model="email" placeholder="Enter Email">
    <input type="password" v-model="password" placeholder="Enter Password">
    <button @click="login">Login</button>
    <p ><router-link to="/sign-up">Sign Up</router-link>
</p>
</div>
</template>

<script setup>
    import axios from 'axios'
    import router from '/src/router.js'
    import { onMounted ,ref } from 'vue';
// import { RouterLink } from 'vue-router';
    const email = ref('');
    const password = ref('');    

    async function login(){
        // console.log(email.value, password.value)
        let res = await axios.get(
            `http://localhost:3000/user?email=${email.value}&password=${password.value}`
        )
        if(res.status==200 && res.data.length>0){
        localStorage.setItem("user-info",JSON.stringify(res.data[0]))
        router.push({name:'Home'})
    }
        console.log(res);
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