<script setup lang="ts">
import { ref } from 'vue';
import { useScroll } from '@vueuse/core';

const scrollBox = ref(null);
const scroll = useScroll(scrollBox);
</script>

<template>
  <div class="scroll-box" ref="scrollBox">
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi
    facilisisMorbi facilisisMorbiddddddddddddddddddddddddddddddddddddddd
    facilisisMorbi Morbi facilisisMorbi facilisisMorbi facilisisfacilisisMorbi
    facilisis lorem felis mauris, vel dapibus nulla molestie laoreet. Nunc
    porttitor metus faucibus ante pellentesque, ac maximus augue cursus. Fusce
    hendrerit, eros dictum accumsan hendrerit.
  </div>
  <pre>  {{ scroll }}</pre>
</template>

<style>
.scroll-box {
  background: gray;
  height: 150px;
  width: 200px;
  overflow: scroll;
  position: relative;
  padding: 10px;
}
</style>
