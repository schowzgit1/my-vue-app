<script setup>
import { ref, onMounted } from 'vue'

const studentData = ref(null)
const loading = ref(false)

const loadData = async () => {
  loading.value = true
  try {
    const response = await fetch('/test-data.json')
    studentData.value = await response.json()
  } catch (e) {
    console.error('Error:', e)
  }
  loading.value = false
}

onMounted(() => {
  loadData()
})
</script>

<template>
  <div class="data-viewer">
    <h2>Project Informatie</h2>
    <button @click="loadData" :disabled="loading">
      {{ loading ? 'Laden...' : 'Ververs Data' }}
    </button>

    <div v-if="studentData" class="info-container">
      <div class="student-info">
        <h3>Student Gegevens:</h3>
        <p>Naam: {{ studentData.studentInfo.naam }}</p>
        <p>Student Nummer: {{ studentData.studentInfo.studentNummer }}</p>
        <p>Datum: {{ studentData.studentInfo.datum }}</p>
        <p>Opleiding: {{ studentData.studentInfo.opleiding }}</p>
      </div>

      <div class="project-info">
        <h3>Project Details:</h3>
        <p>Project: {{ studentData.projectInfo.naam }}</p>
        <p>Framework: {{ studentData.projectInfo.framework }}</p>
        <p>Versie: {{ studentData.projectInfo.versie }}</p>
        <p>Status: {{ studentData.projectInfo.status }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.data-viewer {
  background: #f8f9fa;
  padding: 20px;
  border-radius: 8px;
  margin: 20px 0;
}

.info-container {
  margin-top: 20px;
  text-align: left;
}

.student-info, .project-info {
  margin: 10px 0;
  padding: 15px;
  background: white;
  border-radius: 4px;
}

button {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
}

button:disabled {
  background-color: #999;
}
</style> 