<script setup lang="ts">
import { useSessionStorage } from '@vueuse/core';
const favoriteFood = useSessionStorage('favoriteFood', 'ice');
</script>

<template>
  <input type="text" v-model="favoriteFood" />
</template>
