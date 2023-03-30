<script setup lang="ts">
import { ref, computed } from 'vue';
import { useTimestamp, useInterval } from '@vueuse/core';
const timestamp = useTimestamp();
const counter = useInterval(1000);
const start = Date.now();
const secondsPassed = computed(() => {
  return Math.floor((timestamp.value - start) / 1000);
});
const hangTheBrowser = () => {
  for (let i = 0; i < 1_000_000; i++) {
    console.log(i);
  }
};
</script>

<template>
  <div>Interval: {{ counter }}</div>
  <div>Timestamp: {{ secondsPassed }}</div>
  <button @click="hangTheBrowser">Hang the Browser</button>
</template>
