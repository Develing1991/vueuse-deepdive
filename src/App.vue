<script setup>
import { ref } from 'vue';
import { useClipboard } from '@vueuse/core';

const textToCopy = ref('Hello');
// const { copy, copied, text, isSupported } = useClipboard({
//   source: textToCopy,
//   copiedDuring: 5000, // copied during time // default 2s
// });
const { copy, copied, text, isSupported } = useClipboard({
  copiedDuring: 5000, // copied during time // default 2s
});
</script>

<template>
  <input type="text" v-model="textToCopy" />
  <!-- <button @click="copy()">{{ copied ? 'Copied' : 'Copy' }}</button> -->
  <button @click="copy(textToCopy)">{{ copied ? 'Copied' : 'Copy' }}</button>
  <div>copied text : {{ text }}</div>
  <div>isSupported : {{ isSupported }}</div>
</template>

<style scoped></style>
