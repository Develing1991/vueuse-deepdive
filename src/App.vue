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
      from: 'translateX(100%)',
      to: 'translateX(-100%)',
    };
  } else {
    return {
      from: 'translateX(-100%)',
      to: 'translateX(100%)',
    };
  }
});
</script>

<template>
  <div class="wrapper">
    <div class="carousel">
      <img v-for="image in images" style="display: none" :src="image" />
      <transition>
        <img :src="state" alt="" :key="state" />
      </transition>
    </div>
    <button @click="prev()">&lt;</button>
    <button class="next" @click="next()">&gt;</button>
  </div>
</template>

<style>
body {
  background: #212121;
}
.carousel {
  position: relative;
  height: 200px;
}
img {
  position: absolute;
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 5px;
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
.wrapper {
  position: relative;
}
button {
  position: absolute;
  display: block;
  top: 50%;
  transform: translateY(-50%) scaleX(0.6);
  font-size: 4rem;
  opacity: 0.5;
  transition: 0.2s ease all;
  background: none;
  color: white;
  width: 50px;
  height: 100%;
  appearance: none;
  border: none;
  cursor: pointer;
}
button:hover {
  opacity: 1;
}
button:focus {
  border: none;
}
.next {
  right: 0;
}
</style>
