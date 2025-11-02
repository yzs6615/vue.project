<script setup lang="ts">
import { defineProps, withDefaults } from 'vue'
import { RouterLink } from 'vue-router'

const props = withDefaults(
  defineProps<{
    resource?: string
  }>(),
  {
    resource: 'page',
  },
)
</script>

<template>
  <div>
    <h1>Oops!</h1>
    <h1>哎呀！</h1>
    <h3>The {{ resource }} you're looking for is not here.</h3>
    <h3>您要找的 {{ resource }} 不在这里。</h3>
    <RouterLink :to="{ name: 'event-list-view' }">Back to the home page</RouterLink>
    <RouterLink :to="{ name: 'event-list-view' }">返回首页</RouterLink>
  </div>
</template>

<style scoped>
h1 {
  color: #42b983;
  margin: 20px 0;
}

h3 {
  color: #2c3e50;
  margin: 20px 0;
}

a {
  display: inline-block;
  margin-top: 20px;
  padding: 10px 20px;
  background-color: #42b983;
  color: white;
  text-decoration: none;
  border-radius: 4px;
}

a:hover {
  background-color: #35a873;
}
</style>

