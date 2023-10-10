<script setup lang="ts">
import { ref } from 'vue'

const count = ref(1)
</script>

<template>
  <div>
    <h1>Counter</h1>
    <p>Count: {{ count }}</p>
    <button @click="count++">Increment</button>
  </div>
</template>

<style scoped>

</style>