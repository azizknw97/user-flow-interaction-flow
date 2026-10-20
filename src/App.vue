
<script setup>
import { ref } from 'vue'

const username = ref('')
const password = ref('')
const message = ref('')

function login() {
  if (!username.value || !password.value) {
    message.value = 'Username dan password wajib diisi!'
  } else {
    message.value = `Selamat datang, ${username.value}!`
  }
}
</script>

<template>
  <div class="container">
    <div class="card">
      <h1>Login</h1>
      <p class="subtitle">User Flow & Interaction Flow</p>

      <form @submit.prevent="login">
        <label>Username</label>
        <input
          v-model="username"
          type="text"
          placeholder="Masukkan username"
        />

        <label>Password</label>
        <input
          v-model="password"
          type="password"
          placeholder="Masukkan password"
        />

        <button type="submit">Login</button>
      </form>

      <p v-if="message" class="message">
        {{ message }}
      </p>

      <div class="flow">
        <h3>User Flow</h3>
        <p>Buka halaman → Isi form → Klik Login</p>
      </div>
    </div>
  </div>
</template>
