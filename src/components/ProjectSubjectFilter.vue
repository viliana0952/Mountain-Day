<script setup>
import { ref } from 'vue'

const query = ref('')
const emit = defineEmits(['filter-trails'])

function updateFilter() {
  emit('filter-trails', query.value)
}
</script>

<template>
  <div class="input-wrapper">
    <input v-model="query" @input="updateFilter" type="text" placeholder="Търси по име..." />
  </div>
</template>

<style scoped>
.input-wrapper {
  padding: 20px;
}

input {
  padding: 10px;
  width: 100%;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-sizing: border-box;
}
</style>
