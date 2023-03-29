<script setup>
import { useTitle } from '@vueuse/core';
const title = useTitle();
title.value = 'vueuse title';
console.log('page title', title.value);
</script>

<template>
  <input type="text" v-model="title" />
</template>

<style scoped></style>
