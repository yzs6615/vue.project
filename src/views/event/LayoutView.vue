<script setup lang="ts">
import { provide } from 'vue'
import { RouterLink, RouterView, useRoute } from 'vue-router'
import { useEventStore } from '@/stores/event'
import { storeToRefs } from 'pinia'
import type { Ref } from 'vue'
import type { Event } from '../../types'

const route = useRoute()
const store = useEventStore()
const { event } = storeToRefs(store)
const id = route.params.id as string

// 提供 event 给子组件使用
provide('event', event as Ref<Event | null>)
</script>

<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <nav>
      <RouterLink :to="{ name: 'event-detail-view', params: { id } }">Details</RouterLink>
      |
      <RouterLink :to="{ name: 'event-register-view', params: { id } }">Register</RouterLink>
      |
      <RouterLink :to="{ name: 'event-edit-view', params: { id } }">Edit</RouterLink>
    </nav>
    <RouterView />
  </div>
</template>

<style scoped>
nav {
  margin: 20px 0;
}
nav a {
  text-decoration: none;
  color: #2c3e50;
  margin: 0 10px;
}
nav a.router-link-active {
  color: #42b983;
  font-weight: bold;
}
</style>
