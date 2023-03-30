<script setup lang="ts">
import { ref } from 'vue';
import { useIntervalFn, useRafFn } from '@vueuse/core';
const activePosition = ref(0);
const framesComplete = ref(0);
// const { pause, resume, isActive } = useIntervalFn(() => {
// 기본 1초에 60프레임 사용
const { pause, resume, isActive } = useRafFn(() => {
  framesComplete.value++;
  // 60프레임을 6으로 나눴으니 1초에 10프레임씩 동작
  if (framesComplete.value % 6) return; // 나머지가 0이면 동작 나머지는 truthy하니 리턴
  console.log(framesComplete.value);
  if (activePosition.value > -525) {
    // 7 times frame
    activePosition.value -= 75;
  } else {
    activePosition.value = 0;
  }
});
</script>

<template>
  <button @click="isActive ? pause() : resume()">Toggle</button>
  <div
    class="sprite"
    :style="`background-position: ${activePosition}px 50%;`"
  ></div>
</template>

<style>
.sprite {
  background: url(https://freesvg.org/img/1525205509.png) no-repeat;
  width: 75px;
  height: 150px;
  /* background-position: -150px 50%; */
}
</style>
