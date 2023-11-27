<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { useAuthStore } from '@/stores/auth';
import axios from 'axios';

const auth = useAuthStore()
const username = ref('')
const password = ref('')

const router = useRouter() 

const onLogin = async ()=> {
    // Send a POST request
    const response = await axios({
    method: 'post',
    url: 'http:/localhost:3000/login',
    data: {
        username: username.value,
        password: password.value,
    }
    // data: {
    //     firstName: 'Fred',
    //     lastName: 'Flintstone'
    // }
    });

    console.log(response)
    // auth.login(username.value)

    // router.push('/')
}
</script>
<template>
    <h1>Login Page</h1>
    <div>
        <input type="text" v-model="username" placeholder="username">
        <input type="text" v-model="password" placeholder="password">
        <button @click="onLogin()">Login</button>
    </div>
</template>