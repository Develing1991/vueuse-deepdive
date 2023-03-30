<script setup lang="ts">
import { useLocalStorage } from '@vueuse/core';
const name = useLocalStorage('name', 'lee');
</script>

<template>
  <input type="text" v-model="name" />
</template>
