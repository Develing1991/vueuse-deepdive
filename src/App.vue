<script setup lang="ts">
import { useInterval } from '@vueuse/core';
import { watch } from 'vue';

const { counter, pause, resume, isActive } = useInterval(100, {
  controls: true,
});
watch(counter, () => console.log('hello'));
</script>

<template>
  {{ counter }}
  <button @click="isActive ? pause() : resume()">
    {{ isActive ? 'pause' : 'resume' }}
  </button>
  <button @click="counter = 0">Reset</button>
</template>
