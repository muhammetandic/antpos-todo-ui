<script setup lang="ts">
import { reactive } from 'vue'
import FormInput from '../components/base/FormInput.vue'
import FormButton from '../components/base/FormButton.vue'

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
    <FormInput v-model="formData.email" label="E-Posta" type="text" />
    <FormInput v-model="formData.password" label="Parola" type="password" />

    <FormButton @click="handleSubmit" label="Giriş" />
  </form>
</template>
