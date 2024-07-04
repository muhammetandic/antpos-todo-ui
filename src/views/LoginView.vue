<script setup lang="ts">
import { reactive } from 'vue'
const formData = reactive({ email: '', password: '', authType: 'cookie' })
const handleSubmit = () => {
  console.log(formData)
  fetch('http://localhost:5200/auth/signin', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(formData)
  })
    .then((response) => console.log(response.json()))
    .catch((error) => console.log(error))
}
</script>

<template>
  <form @submit.prevent="handleSubmit">
    <div>
      <label>Kullanıcı Adı</label>
      <input type="text" v-model="formData.email" />
    </div>
    <div>
      <label>Parola</label>
      <input type="password" v-model="formData.password" />
    </div>

    <button type="submit" @click="handleSubmit">Giriş</button>
  </form>
</template>

<style scoped>
label {
  display: block;
  margin-top: 1rem;
  margin-bottom: 0.3rem;
}

input,
button {
  border-radius: 0.25rem;
  font-size: 1.25rem;
  padding: 0.25rem;
  border: none;
}

input {
  min-width: 25rem;
  border: 2px solid var(--primary-color);
}

input:focus {
  outline: none;
  border: 2px solid var(--input-color);
}

button {
  background: var(--primary-color);
  min-width: 5rem;
  cursor: pointer;
  margin-top: 1rem;
}

button:hover {
  background: var(--input-color);
}
</style>
