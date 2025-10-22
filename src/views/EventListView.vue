<script setup lang="ts">
import EventCard from '../components/EventCard.vue'
import EventInfo from '../components/EventInfo.vue'
import type { Event } from '../types'
import { ref, onMounted } from 'vue'
import EventService from '../services/EventService'

const events = ref<Event[]>([])

// 临时静态数据，用于显示页面
const tempEvents: Event[] = [
  {
    id: 5928101,
    category: 'animal welfare',
    title: 'Cat Adoption Day',
    description: 'Find your new feline friend at this event.',
    location: 'Meow Town',
    date: 'January 28, 2022',
    time: '12:00',
    petsAllowed: true,
    organizer: 'Kat Laydee'
  },
  {
    id: 4582797,
    category: 'food',
    title: 'Community Gardening',
    description: 'Join us as we tend to the community edible plants.',
    location: 'Flora City',
    date: 'March 14, 2022',
    time: '10:00',
    petsAllowed: true,
    organizer: 'Fern Pollin'
  }
]

onMounted(() => {
  EventService.getEvents()
    .then((response) => {
      events.value = response.data
    })
    .catch((error) => {
      console.error('There was an error loading from server:', error)
      // 如果服务器失败，使用静态数据作为后备
      events.value = tempEvents
    })
})
</script>

<template>
  <div>
    <h1>Events For Good</h1>
    <!-- new element -->
    <!-- 新元素 -->
    
    <div class="events">
      <EventCard v-for="event in events" :key="event.id" :event="event" />
      <EventInfo v-for="event in events" :key="`info-${event.id}`" :event="event" />
    </div>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
