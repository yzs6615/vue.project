<script setup lang="ts">
import { inject } from 'vue'
import type { Ref } from 'vue'
import type { Event } from '../../types'
import { useMessageStore } from '@/stores/message'
import { storeToRefs } from 'pinia'

const event = inject<Ref<Event | null>>('event')
const store = useMessageStore()
const { message } = storeToRefs(store)
</script>

<template>
  <div v-if="event">
    <div id="flashMessage" class="animate-fade" v-if="message">
      <h4>{{ message }}</h4>
    </div>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<style scoped>
/* All styles have been replaced with Tailwind CSS classes */
</style>
