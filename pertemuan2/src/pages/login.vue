<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { useAuthStore } from '@/stores/auth';
import axios from 'axios';

const auth = useAuthStore()
const username = ref('')
const password = ref('')

const router = useRouter() 

const onLogin = async () => {
  try {
    const response = await axios.post('http://localhost:3000/login', {
      username: username.value,
      password: password.value,
    })
    
    auth.login(username.value)
    console.log(response);
  } catch (error) {
    console.error('Login error:', error);
  }
}
console.log(Response)
</script>
<template>
    <h1>Login Page</h1>
    <div>
        <input type="text" v-model="username" placeholder="username">
        <input type="text" v-model="password" placeholder="password">
        <button @click="onLogin()">Login</button>
    </div>
</template>