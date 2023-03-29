<script setup>
import { ref } from 'vue';
import { onKeyStroke } from '@vueuse/core';
const position = ref({ x: 0, y: 0 });
const controls = {
  ArrowDown: () => (position.value.y += 5),
  ArrowUp: () => (position.value.y -= 5),
  ArrowRight: () => (position.value.x += 5),
  ArrowLeft: () => (position.value.x -= 5),
};
onKeyStroke(Object.keys(controls), (e) => {
  e.preventDefault();
  controls[e.key]();
});
// onKeyStroke(['ArrowDown', 'ArrowUp', 'ArrowRight', 'ArrowLeft'], (e) => {
//   e.preventDefault();
//   //ArrowDown...
//   if (e.key === 'ArrowDown') {
//     position.value.y += 5;
//   }
//   if (e.key === 'ArrowUp') {
//     position.value.y -= 5;
//   }
//   if (e.key === 'ArrowRight') {
//     position.value.x += 5;
//   }
//   if (e.key === 'ArrowLeft') {
//     position.value.x -= 5;
//   }
// });
// onKeyStroke('ArrowDown', (e) => {
//   e.preventDefault();
//   position.value.y += 5;
// });
// onKeyStroke('ArrowUp', (e) => {
//   e.preventDefault();
//   position.value.y -= 5;
// });
</script>

<template>
  <div class="ball"></div>
  <input type="text" />
</template>

<style>
.ball {
  width: 10px;
  height: 10px;
  background: red;
  border-radius: 50%;
  position: absolute;
  top: v-bind(position.y + 'px');
  left: v-bind(position.x + 'px');
}
</style>
