<script setup lang="ts">
import { computed } from 'vue';
import { useIntervalFn } from '@vueuse/core';
import { useAppCycleList } from './useAppCycleList';
const images = [
  'https://tinyurl.com/2p8dav94',
  'https://tinyurl.com/2p9yrrhs',
  'https://tinyurl.com/ycxurpah',
];
const { state, next, prev, isForward, isBackward } = useAppCycleList(images);

useIntervalFn(() => next(), 3000);

const direction = computed(() => {
  if (isForward.value) {
    return {
      from: `translateX(100%)`,
      to: `translateX(-100%)`,
    };
  } else {
    return {
      from: `translateX(-100%)`,
      to: `translateX(100%)`,
    };
  }
});
</script>

<template>
  <img v-for="image in images" style="display: none" :src="image" alt="" />
  <div class="carousel">
    <transition>
      <img :src="state" alt="" :key="state" />
    </transition>
  </div>
  <button @click="prev()">Prev</button>
  <button @click="next()">Next</button>
</template>

<style>
.carousel {
  position: relative;
  height: 200px;
}
img {
  position: absolute;
  width: 100%;
  height: 200px;
  object-fit: cover;
}
.v-enter-active,
.v-leave-active {
  transition: all 0.5s ease;
}

.v-enter-from {
  transform: v-bind('direction.from');
}
.v-leave-to {
  transform: v-bind('direction.to');
}
</style>
