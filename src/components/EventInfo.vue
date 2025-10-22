<script setup lang="ts">
import type { Event } from '../types'

const props = defineProps<{
  event: Event
}>()
</script>

<template>
  <div class="event-info">
    <p>{{ event.category }}</p>
    <p>{{ event.organizer }}</p>
  </div>
</template>

<style scoped>
.event-info {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 5px;
}

.event-info p {
  margin: 0;
  font-size: 14px;
  text-align: right;
}
</style>
