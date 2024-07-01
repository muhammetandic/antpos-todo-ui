<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue'
import SunIcon from './components/icons/SunIcon.vue'
import MoonIcon from './components/icons/MoonIcon.vue'

const isDark = localStorage.getItem('darkMode') === 'true' ? true : false
document.documentElement.setAttribute('data-theme', isDark ? 'dark' : 'light')

const darkMode = ref(isDark)
const toggleTheme = () => {
  darkMode.value = !darkMode.value
  document.documentElement.setAttribute('data-theme', darkMode.value ? 'dark' : 'light')
  localStorage.setItem('darkMode', darkMode.value)
}
</script>

<template>
  <div class="app">
    <header>
      <div class="wrapper">
        <nav>
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/about">About</RouterLink>
        </nav>
        <SunIcon v-if="darkMode" @click="toggleTheme" class="icon" width="24px" height="24px" />
        <MoonIcon v-else @click="toggleTheme" class="icon" width="24px" height="24px" />
      </div>
      <hr />
    </header>

    <RouterView />
  </div>
</template>

<style scoped>
.app {
  max-width: 960px;
  margin: 0 auto;
}

.wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.icon {
  cursor: pointer;
}

nav a {
  font-weight: bold;
  text-decoration: none;
  color: var(--primary-color);
  margin: 0 8px 0 0;
}
</style>
