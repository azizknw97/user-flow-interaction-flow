
<script setup>
import { ref } from 'vue'

const email = ref('')
const password = ref('')
const pesan = ref('')
const tipePesan = ref('')
const berhasilLogin = ref(false)

function login() {
  if (email.value.trim() === '' || password.value === '') {
    pesan.value = 'Email dan password wajib diisi!'
    tipePesan.value = 'error'
    return
  }

  if (
    email.value === 'mahasiswa@kampus.ac.id' &&
    password.value === '12345'
  ) {
    pesan.value = 'Login berhasil!'
    tipePesan.value = 'success'
    berhasilLogin.value = true
  } else {
    pesan.value = 'Email atau password salah!'
    tipePesan.value = 'error'
  }
}

function logout() {
  email.value = ''
  password.value = ''
  pesan.value = ''
  tipePesan.value = ''
  berhasilLogin.value = false
}
</script>

<template>
  <main class="page-container">
    <section class="login-card">
      <div class="brand-icon">
        <span>U</span>
      </div>

      <div class="heading">
        <h1 v-if="!berhasilLogin">Selamat Datang!</h1>
        <h1 v-else>Dashboard</h1>

        <p v-if="!berhasilLogin">
          Silakan masuk ke akun mahasiswa Anda.
        </p>
        <p v-else>
          Anda berhasil masuk ke aplikasi.
        </p>
      </div>

      <div v-if="!berhasilLogin" class="form-container">
        <form @submit.prevent="login">
          <div class="form-group">
            <label for="email">Email</label>
            <input
              id="email"
              v-model="email"
              type="email"
              placeholder="nama@kampus.ac.id"
            />
          </div>

          <div class="form-group">
            <label for="password">Password</label>
            <input
              id="password"
              v-model="password"
              type="password"
              placeholder="Masukkan password"
            />
          </div>

          <button type="submit" class="btn-primary">
            Login
          </button>
        </form>

        <div
          v-if="pesan"
          class="message"
          :class="tipePesan"
          role="status"
        >
          {{ pesan }}
        </div>

        <div class="demo-info">
          <strong>Akun untuk simulasi</strong>
          <p>Email: mahasiswa@kampus.ac.id</p>
          <p>Password: 12345</p>
        </div>
      </div>

      <div v-else class="dashboard-content">
        <div class="success-icon">✓</div>

        <h2>Login Berhasil</h2>
        <p class="welcome-message">
          Selamat datang, mahasiswa!
        </p>

        <div class="account-info">
          <span>Email Anda</span>
          <strong>{{ email }}</strong>
        </div>

        <button
          type="button"
          class="btn-secondary"
          @click="logout"
        >
          Logout
        </button>
      </div>

      <footer>
        <p>Demo User Flow & Interaction Flow</p>
        <p>Vue.js Learning Project</p>
      </footer>
    </section>
  </main>
</template>
