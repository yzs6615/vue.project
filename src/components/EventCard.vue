<script setup lang="ts">
import type { Event } from '../types'

const props = defineProps<{
  event: Event
}>()
</script>

<template>
  <div class="event-class">
    <div class="event-card">
      <h2>{{ event.title }}</h2>
      <p class="category">{{ event.category }}</p>
      <p class="description">{{ event.description }}</p>
      <p class="location">📍 {{ event.location }}</p>
      <span class="datetime">@{{ event.time }} on {{ event.date }}</span>
    </div>
  </div>
</template>

<style scoped>
.event-card {
  padding: 20px;
  width: 250px;
  cursor: pointer;
  border: 1px solid #39495c;
  margin-bottom: 18px;
  background: white;
  border-radius: 8px;
}

.event-card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
}

.event-card h2 {
  margin: 0 0 10px 0;
  color: #2c3e50;
}

.category {
  margin: 5px 0;
  font-size: 12px;
  color: #666;
  text-transform: uppercase;
  font-weight: bold;
}

.description {
  margin: 10px 0;
  font-size: 14px;
  color: #555;
  line-height: 1.4;
}

.location {
  margin: 8px 0;
  font-size: 14px;
  color: #42b983;
  font-weight: 500;
}

.datetime {
  display: block;
  margin-top: 15px;
  font-size: 13px;
  color: #888;
  font-style: italic;
}
</style>

