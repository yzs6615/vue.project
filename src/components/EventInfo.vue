<script setup lang="ts">
import type { Event } from '../types'

const props = defineProps<{
  event: Event
}>()
</script>

<template>
  <div class="flex flex-col items-end gap-[5px]">
    <p class="m-0 text-sm text-right">{{ event.category }}</p>
    <p class="m-0 text-sm text-right">{{ event.organizer }}</p>
  </div>
</template>

<style scoped>
/* All styles have been replaced with Tailwind CSS classes */
</style>
