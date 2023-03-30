<script setup>
import { ref, reactive, watch, onMounted } from 'vue';
import { onLongPress } from '@vueuse/core';
const longBtn = ref(null);
onLongPress(
  longBtn,
  () => {
    alert('Hello world');
  },
  {
    delay: 3000,
  }
);
</script>

<template>
  <button ref="longBtn">Click and Hold</button>
</template>

<style></style>
