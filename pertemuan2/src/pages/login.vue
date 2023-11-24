<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { useAuthStore } from '@/stores/auth';

const auth = useAuthStore()
const username = ref('')

const router = useRouter() 

const onLogin = ()=> {
    auth.login(username.value)

    router.push('/')
}
</script>
<template>
    <h1>Login Page</h1>
    <div>
        <input type="text" v-model="username">
        <button @click="onLogin()">Login</button>
    </div>
</template>