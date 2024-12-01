<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  }
})
</script>

<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<style scoped>

header {
  background-color: #4CAF50;
  color: white;
  padding: 10px;
  font-size: 1.5em;
  text-align: center;
}

h1 {
  font-family: 'Nunito', sans-serif; 
  font-size: 3rem;
  color: #2e7d32;
  letter-spacing: 1px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1); 
  margin: 0;
}

</style>
