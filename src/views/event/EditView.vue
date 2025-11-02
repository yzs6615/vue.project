<script setup lang="ts">
import { inject } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import type { Ref } from 'vue'
import type { Event } from '../../types'
import { useMessageStore } from '@/stores/message'

const route = useRoute()
const router = useRouter()
const store = useMessageStore()

const event = inject<Ref<Event | null>>('event')

const goToDetails = () => {
  if (event?.value) {
    store.updateMessage('Event data has been updated / 事件数据已更新')

    setTimeout(() => {
      store.resetMessage()
    }, 3000)

    router.push({ name: 'event-detail-view', params: { id: event.value.id } })
  }
}
</script>

<template>
  <div v-if="event">
    <p>Edit event here</p>
    <p>在此处编辑事件</p>
    <button @click="goToDetails">Save Changes</button>
  </div>
</template>

<style scoped>
button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #35a873;
}
</style>
