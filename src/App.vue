<script setup lang="ts">
import { ref } from 'vue';
import { useTransition, TransitionPresets } from '@vueuse/core';
const percent = ref(0);
const disabled = ref(false);
const color = ref('blue');
const animatedPercent = useTransition(percent, {
  transition: TransitionPresets.easeInOutCubic,
  duration: 3000,
  disabled,
  onStarted() {},
  onFinished() {
    color.value = 'green';
  },
});
const load = () => {
  percent.value = 100;
};
</script>

<template>
  <div
    class="loading"
    :style="`width: ${animatedPercent}%; background: ${color}`"
  ></div>
  {{ Math.floor(animatedPercent) }} %
  <button @click="load">Load</button>
  <button @click="disabled = true">disabled</button>
</template>

<style>
.loading {
  height: 10px;
  /* background: "blue" */
}
</style>
