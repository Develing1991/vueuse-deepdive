<script setup>
import { ref, reactive, watch, onMounted } from 'vue';
import { usePointer } from '@vueuse/core';

const pointer = reactive(usePointer());
const canvas = ref(null);
watch(pointer, () => {
  if (pointer.pressure === 0) return;
  const ctx = canvas.value.getContext('2d');
  ctx.fillStyle = 'red';
  ctx.fillRect(pointer.x - 20, pointer.y - 20, 10, 10);
});
onMounted(() => {
  canvas.value.height = document.body.clientHeight;
  canvas.value.width = document.body.clientWidth;
});
</script>

<template>
  <canvas ref="canvas"></canvas>
  <!-- <pre>  {{ pointer }}</pre> -->
</template>

<style></style>
