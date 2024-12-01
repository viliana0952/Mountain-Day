<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  name: String,
  imageSrc: String,
  description: String,
  index: Number
})

const emit = defineEmits()

function deleteSubject() {
  emit('delete', props.index)
}
</script>

<template>
  <div class="project-subject-card">
    <h2>{{ name }}</h2>
    <div class="content-wrapper">
      <img class="image" :src="imageSrc" alt="Image" />
      <span class="description">{{ description }}</span>
      <button @click="deleteSubject">Delete</button> 
    </div>
  </div>
</template>

<style scoped>

.project-subject-card {
  background: #66bb6a;
  border-radius: 8px;
  padding: 10px;
  margin: 10px;
  width: 100%;
  color: white;
  transition: box-shadow 0.3s ease;
}

.project-subject-card:hover {
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}

h2 {
  padding-bottom: 12px;
  color: #2e7d32;
  font-weight: 900;
}

.content-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 12px;
}

.description {
  flex-grow: 1;
}

.image {
  height: 100px;
  width: auto;
}

button {
  background-color: #C6011F;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 1rem;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
  align-self: end;
}

button:hover {
  background-color: darkred; 
}

</style>
