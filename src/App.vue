<script setup lang="ts">
import { useIntervalFn } from '@vueuse/core';

const { pause, resume, isActive } = useIntervalFn(
  () => console.log('hello'),
  100
);
</script>

<template>
  <button @click="isActive ? pause() : resume()">
    {{ isActive ? 'pause' : 'resume' }}
  </button>
</template>
