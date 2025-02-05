<script setup>
import JsonViewer from './components/JsonViewer.vue'
</script>

<template>
  <div class="app">
    <h1>Framework Test Project</h1>
    <JsonViewer />
  </div>
</template>

<style scoped>
.app {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

h1 {
  color: #2c3e50;
  text-align: center;
  margin-bottom: 2rem;
}
</style>
