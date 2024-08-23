<script setup lang="ts">
const props = defineProps({
  label: String
})

const emit = defineEmits(['click'])

const handleClick = (e: Event) => {
  e.preventDefault()
  emit('click')
}

const { label } = props
</script>

<template>
  <div>
    <button @click="handleClick">{{ label }}</button>
  </div>
</template>

<style scoped>
div {
  margin-top: 1rem;
}

button {
  border-radius: 0.25rem;
  font-size: 1.25rem;
  padding: 0.25rem;
  border: none;
  background: var(--primary-color);
  min-width: 5rem;
  cursor: pointer;
  margin-top: 1rem;
}

button:hover {
  background: var(--input-color);
}
</style>
