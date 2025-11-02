<script setup lang="ts">
import { RouterLink } from 'vue-router'
import EventCard from '../components/EventCard.vue'
import EventInfo from '../components/EventInfo.vue'
import type { Event } from '../types'
import { ref, computed, watchEffect } from 'vue'
import EventService from '../services/EventService'

defineOptions({
  name: 'EventListView',
})

const events = ref<Event[] | null>(null)
const totalEvents = ref(0)

const props = defineProps({
  page: {
    type: Number,
    required: true,
  },
})

const page = computed(() => props.page)

const hasNextPage = computed(() => {
  const totalPages = Math.ceil(totalEvents.value / 3)
  return page.value < totalPages
})

watchEffect(() => {
  EventService.getEvents(3, page.value)
    .then((response) => {
      events.value = response.data
      totalEvents.value = parseInt(response.headers['x-total-count'] || '8')
    })
    .catch((error) => {
      console.error('There was an error!', error)
      console.error('出现错误！', error)
    })
})
</script>

<template>
  <div>
    <h1>Events For Good</h1>

    <div v-if="!events" class="text-center p-4">
      <p>加载中...</p>
    </div>

    <div v-else-if="events.length === 0" class="text-center p-4">
      <p>暂无事件数据</p>
    </div>

    <div v-else class="flex flex-col items-center">
      <EventCard v-for="event in events" :key="event.id" :event="event" />
      <EventInfo v-for="event in events" :key="`info-${event.id}`" :event="event" />
    </div>

    <div v-if="events" class="flex w-[290px] mx-auto">
      <RouterLink
        id="page-prev"
        class="flex-1 no-underline text-gray-700 text-left"
        :to="{ name: 'event-list-view', query: { page: page - 1 } }"
        rel="prev"
        v-if="page != 1"
      >
        &#60; Prev Page
      </RouterLink>

      <RouterLink
        id="page-next"
        class="flex-1 no-underline text-gray-700 text-right"
        :to="{ name: 'event-list-view', query: { page: page + 1 } }"
        rel="next"
        v-if="hasNextPage"
      >
        Next Page &#62;
      </RouterLink>
    </div>
  </div>
</template>

<style scoped>
/* All styles have been replaced with Tailwind CSS classes */
</style>
