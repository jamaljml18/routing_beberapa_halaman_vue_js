<script setup lang="ts">
import { ref } from 'vue';
import { useAuthStore } from '@/stores/auth';
import { useRouter } from 'vue-router';

const auth = useAuthStore()
const router = useRouter()

const onLogout = () => {
  auth.logout()
  router.push('/login')
}

</script>
<template>
  <div class="box">
    <!-- Header -->
    <div class="header">
      <!-- Menu -->
      <div class="home_about_button">
        <router-link to="/" class="home_button">home button</router-link>
        <router-link to ="/about" class="about_button">about button</router-link>
        <router-link to ="/restricted" class="restricted_button">restricted button</router-link>
      </div>
      <!-- Authentication User -->
      <div class="a_login_button">
        <div><p v-if="auth.username">{{ auth.username }}</p></div>
        <div v-if="auth.username">
          <button class="logout_button" @click="onLogout">Logout</button>
        </div>
        <div v-else="">
          <router-link to="/login" class="login_button">Login</router-link>
        </div>
      </div>
    </div>
    <!-- Body -->
    <router-view></router-view>
  </div>
</template>