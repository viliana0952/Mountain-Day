<script setup>
import { defineProps, defineEmits } from 'vue'
import ProjectSubjectCard from './ProjectSubjectCard.vue'

// Define the props to accept an array of ProjectSubjects from the parent
const props = defineProps({
  projectSubjects: Array
})

// Define the event emitter to communicate with the parent
const emit = defineEmits()

// Handle the delete action passed from ProjectSubjectCard
function handleDelete(index) {
  emit('delete', index) // Emit the delete event to the parent with the name of the subject to delete
}
</script>

<template>
  <div class="project-subject-list">
    <ProjectSubjectCard
      v-for="(subject, index) in projectSubjects"
      :key="index"
      :name="subject.name"
      :imageSrc="subject.image"
      :description="subject.description"
      @delete="handleDelete(index)"
    />
  </div>
</template>

<style scoped>
.project-subject-list {
  display: flex;
  flex-wrap: wrap;
}
</style>
