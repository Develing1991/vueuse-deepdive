<script setup lang="ts">
import { ref, computed } from 'vue';
import { useIntersectionObserver } from '@vueuse/core';
const h1 = ref(null);
const h1IsVisible = ref(false);
useIntersectionObserver(h1, ([{ isIntersecting }]) => {
  h1IsVisible.value = isIntersecting;
});
</script>

<template>
  <div style="height: 200px; overflow: scroll; border: 1px solid black">
    <h1 :class="{ 'fade-in': h1IsVisible }" style="margin: 300px 0" ref="h1">
      Hello
    </h1>
  </div>
  {{ h1IsVisible }}
</template>

<style>
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
.fade-in {
  animation: fadeIn ease 1s;
}
</style>
