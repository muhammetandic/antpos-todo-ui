<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue'

const darkMode = ref(localStorage.getItem('darkMode') || false)
const toggleTheme = () => {
  darkMode.value = !darkMode.value
  document.documentElement.setAttribute('data-theme', darkMode.value ? 'dark' : 'light')
  localStorage.setItem('darkMode', darkMode.value)
}
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <span @click="toggleTheme">Toggle {{ darkMode ? 'dark' : 'light' }} </span>
      </nav>
    </div>
  </header>

  <RouterView />
</template>
