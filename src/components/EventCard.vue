<script setup lang="ts">
import { RouterLink } from 'vue-router'
import type { Event } from '../types'

const props = defineProps<{
  event: Event
}>()
</script>

<template>
  <RouterLink class="no-underline text-gray-700" :to="{ name: 'event-detail-view', params: { id: event.id } }">
    <div class="cursor-pointer border border-gray-600 p-[20px] w-[250px] mb-[18px] hover:scale-101 hover:shadow-sp bg-white rounded-lg transition-transform">
      <h2 class="m-0 mb-2.5 text-gray-700 text-xl">{{ event.title }}</h2>
      <p class="my-[5px] text-xs text-gray-600 uppercase font-bold">{{ event.category }}</p>
      <p class="my-2.5 text-sm text-gray-600 leading-snug">{{ event.description }}</p>
      <p class="my-2 text-sm text-green-500 font-medium">📍 {{ event.location }}</p>
      <span class="block mt-[15px] text-[13px] text-gray-500 italic">@{{ event.time }} on {{ event.date }}</span>
    </div>
  </RouterLink>
</template>

<style scoped>
/* All styles have been replaced with Tailwind CSS classes */
</style>
