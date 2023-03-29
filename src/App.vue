<script setup>
import { ref } from 'vue';
import { useDark, useToggle, useColorMode } from '@vueuse/core';

// const isDark = useDark(); //true or false
// const toggleDark = useToggle(isDark);
const colorMode = useColorMode({
  modes: {
    // custom mode
    dim: 'dim',
    cafe: 'cafe',
  },
  attribute: 'theme',
}); // light or dark
</script>

<template>
  {{ colorMode }}
  <button @click="colorMode = 'dark'">Dark Mode</button>
  <button @click="colorMode = 'light'">light Mode</button>
  <button @click="colorMode = 'dim'">Dim Mode</button>
  <button @click="colorMode = 'cafe'">Cafe Mode</button>
  <!-- {{ isDark }}
  <br />
  <button @click="toggleDark()">Toggle Dark Mode</button> -->
</template>

<style>
/* .dark {
  background: #252525;
  color: white;
}
.dim {
  background: gray;
  color: white;
}
.cafe {
  background: #c0acac;
  color: black;
} */
[theme='dark'] {
  background: #252525;
  color: white;
}
[theme='dim'] {
  background: gray;
  color: white;
}
[theme='cafe'] {
  background: #c0acac;
  color: black;
}
</style>
