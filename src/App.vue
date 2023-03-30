<script setup>
import { ref, watch } from 'vue';
import { usePageLeave, whenever } from '@vueuse/core';

const isLeft = usePageLeave();
const unwatch = whenever(isLeft, () => {
  alert('Are you sure you want to go?');
  unwatch();
});
</script>

<template>
  <br />
  {{ isLeft }}
</template>

<style></style>
