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

const register = () => {
  // If the registration API call successful
  // 如果注册 API 调用成功
  // Push back to the event details view
  // 返回事件详情视图
  if (event?.value) {
    store.updateMessage(
      'You are successfully registered for ' +
        event.value.title +
        ' / 您已成功注册 ' +
        event.value.title,
    )

    setTimeout(() => {
      store.resetMessage()
    }, 3000)

    router.push({ name: 'event-detail-view', params: { id: event.value.id } })
  }
}
</script>

<template>
  <div v-if="event">
    <h2>Register for {{ event.title }}</h2>
    <p>Register event here</p>
    <p>在此处注册事件</p>
    <button @click="register">Register Me!</button>
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
