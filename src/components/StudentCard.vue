<script setup lang="ts">
import type { Student } from '../types'

const props = defineProps<{
  student: Student
}>()
</script>

<template>
  <div class="p-5 w-[250px] mb-[18px] border border-gray-300 bg-white rounded-lg shadow-md hover:scale-101 hover:shadow-lg transition-transform">
    <h3 class="m-0 mb-2.5 text-gray-700 text-lg">{{ student.firstName }} {{ student.lastName }}</h3>
    <p class="m-0 text-sm text-gray-600 font-bold">GPA: {{ student.gpa }}</p>
  </div>
</template>

<style scoped>
/* All styles have been replaced with Tailwind CSS classes */
</style>

