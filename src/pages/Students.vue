<template>
  <div class="container">
    <!-- STUDENT DIRECTORY -->
    <div class="section-card">
      <h2 class="section-title">Student Directory</h2>

      <div class="student-grid">
        <StudentComponent
          v-for="student in students"
          :key="student.id"
          :name="student.name"
          :course="student.course"
          :year="student.year"
        />
      </div>
    </div>

    <!-- API USERS -->
    <div class="section-card api-section">
      <h2 class="section-title">API Users</h2>

      <p v-if="loading" class="loading">Loading data...</p>
      <p v-if="error" class="error">{{ error }}</p>

      <div v-if="!loading && !error" class="api-grid">
        <div v-for="user in apiUsers" :key="user.id" class="api-card">
          <h4>{{ user.name }}</h4>
          <p>{{ user.email }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import StudentComponent from '../components/StudentComponent.vue'

const students = ref([
  { id: 1, name: 'John Benedict Gapas', course: 'BSIT', year: '4th Year' },
  { id: 2, name: 'Jane Smith', course: 'BSCS', year: '2nd Year' },
  { id: 3, name: 'Michael Cruz', course: 'BSIT', year: '3rd Year' }
])

const apiUsers = ref([])
const loading = ref(true)
const error = ref(null)

onMounted(async () => {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/users')
    if (!response.ok) throw new Error('Failed to fetch API')

    apiUsers.value = await response.json()
  } catch (err) {
    error.value = err.message
  } finally {
    loading.value = false
  }
})
</script>

<style scoped>
.section-card {
  background: white;
  padding: 40px;
  border-radius: 16px;
  box-shadow: 0 8px 24px rgba(0,0,0,0.08);
  margin-bottom: 50px;
}

.section-title {
  margin-bottom: 25px;
  color: #2c3e50;
  font-weight: 600;
}

.student-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.api-section {
  margin-top: 20px;
}

.api-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 15px;
}

.api-card {
  background: #f9f9f9;
  padding: 15px;
  border-radius: 10px;
  transition: 0.3s;
}

.api-card:hover {
  background: #f1f1f1;
}

.loading {
  color: #42b883;
}

.error {
  color: red;
}
</style>
