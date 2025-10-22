<script setup lang="ts">
import type { Student } from '../types'

const props = defineProps<{
  student: Student
}>()
</script>

<template>
  <div class="student-card">
    <h3>{{ student.firstName }} {{ student.lastName }}</h3>
    <p class="gpa">GPA: {{ student.gpa }}</p>
  </div>
</template>

<style scoped>
.student-card {
  padding: 20px;
  width: 250px;
  border: 1px solid #ddd;
  margin-bottom: 18px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.student-card:hover {
  transform: scale(1.01);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

.student-card h3 {
  margin: 0 0 10px 0;
  color: #2c3e50;
  font-size: 18px;
}

.gpa {
  margin: 0;
  font-size: 14px;
  color: #666;
  font-weight: bold;
}
</style>
