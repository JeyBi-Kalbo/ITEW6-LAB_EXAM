<template>
  <div class="student-card">
    <div class="student-header">
      <h3>{{ name }}</h3>
      <span class="year">{{ year }}</span>
    </div>

    <p class="course">{{ course }}</p>

    <button @click="toggleDetails">
      {{ showDetails ? "Hide Info" : "View Info" }}
    </button>

    <div v-if="showDetails" class="details">
      Actively enrolled student.
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

defineProps({
  name: String,
  course: String,
  year: String
})

const showDetails = ref(false)

function toggleDetails() {
  showDetails.value = !showDetails.value
}
</script>

<style scoped>
.student-card {
  background: white;
  padding: 20px;
  border-radius: 14px;
  box-shadow: 0 6px 18px rgba(0,0,0,0.06);
}

.student-header {
  display: flex;
  justify-content: space-between;
}

.year {
  background: #42b883;
  color: white;
  padding: 4px 10px;
  border-radius: 20px;
  font-size: 12px;
}

button {
  background: #42b883;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 8px;
  margin-top: 10px;
  cursor: pointer;
}
</style>
