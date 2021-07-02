<template>
  <div>
    <h1>404 - No Page Here... Sorry</h1>
    <router-link :to="{ name: 'Home' }">Return Home</router-link>
  </div>
</template>

<script>
  export default {
    name: 'NotFound'
  }
</script>

<style scoped>
</style>
