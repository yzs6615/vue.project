<script setup lang="ts">
import { useRouter } from 'vue-router'

const router = useRouter()
</script>

<template>
  <div class="networkError">
    <h1>Uh-Oh!</h1>
    <h1>哎呀！</h1>

    <h3>
      It looks like you're experiencing some network issues, please take a breath and
      看起来您遇到了一些网络问题，请稍作休息并
      <a href="#" @click.prevent="router.go(-1)">click here</a> to try again.
      <a href="#" @click.prevent="router.go(-1)">点击这里</a> 重新尝试。
    </h3>
  </div>
</template>

<style scoped>
.networkError {
  text-align: center;
  padding: 50px 20px;
}

h1 {
  color: #e74c3c;
  margin: 20px 0;
}

h3 {
  color: #2c3e50;
  margin: 20px 0;
  line-height: 1.6;
}

a {
  color: #42b983;
  text-decoration: underline;
  cursor: pointer;
}

a:hover {
  color: #35a873;
}
</style>







