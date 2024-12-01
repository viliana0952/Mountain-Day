<script setup>
import { ref } from 'vue'

const name = ref('')
const image = ref('')
const description = ref('')

const emit = defineEmits(['add-trail'])

function submitForm() {
  if (name.value && image.value && description.value) {
    emit('add-trail', {
      name: name.value,
      image: image.value,
      description: description.value,
    })

    name.value = ''
    image.value = ''
    description.value = ''
  }
}
</script>

<template>
  <form @submit.prevent="submitForm">
    <input v-model="name" type="text" placeholder="Име..." required />
    <input v-model="image" type="text" placeholder="Снимка..." required />
    <textarea v-model="description" placeholder="Описание..." required></textarea>
    <button type="submit">Добави пътека</button>
  </form>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  gap: 20px; /* More space between elements */
  margin: 30px auto;
  min-width: 400px;
  width: 400px;
  padding: 20px;
  border-radius: 8px;
  background-color: #e8f5e9; /* Light pastel green background */
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1); /* Soft shadow for a 3D effect */
}

input, textarea {
  padding: 12px;
  border: 2px solid #81c784; /* Pastel green border */
  border-radius: 6px;
  font-size: 1rem;
  transition: border-color 0.3s ease;
  resize: vertical
}

input:focus, textarea:focus {
  border-color: #4caf50; /* Darker green when focused */
  outline: none;
}

input::placeholder, textarea::placeholder {
  color: #9e9e9e; /* Light grey placeholder */
}

button {
  background-color: #81c784; /* Pastel green background */
  color: white;
  border: none;
  padding: 12px;
  margin-top: 12px;
  font-size: 1.1rem;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
}

button:hover {
  background-color: #66bb6a; /* Slightly darker green when hovering */
}

@media (max-width: 500px) {
  form {
    margin: 15px;
    padding: 15px;
  }

  input, textarea {
    font-size: 0.9rem;
  }

  button {
    font-size: 1rem;
  }
}
</style>

