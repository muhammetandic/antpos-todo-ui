<script setup>
import { toRef, watch } from 'vue'

const props = defineProps({
  label: String,
  type: String,
  modelValue: String
})

const emit = defineEmits(['update:modelValue'])

const model = toRef(props.modelValue)

watch(model, (value) => {
  emit('update:modelValue', value)
})

const { label, type } = props
</script>

<template>
  <div>
    <label>{{ label }}</label>
    <input :type="type" v-model="model" />
  </div>
</template>

<style scoped>
div {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
  margin-top: 1.25rem;
}

label {
  font-size: 1.25rem;
}

input {
  border-radius: 0.25rem;
  font-size: 1.25rem;
  padding: 0.25rem;
  border: none;
  min-width: 25rem;
  border: 2px solid var(--primary-color);
}

input:focus {
  outline: none;
  border: 2px solid var(--input-color);
}
</style>
