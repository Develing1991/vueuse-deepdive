<script setup lang="ts">
import { ref, computed } from 'vue';
import { computedAsync } from '@vueuse/core';
const id = ref(1);
const url = computed(
  () => `https://jsonplaceholder.typicode.com/posts/${id.value}/`
);
const post = computedAsync(async () => {
  // await post.get(id.value)
  const res = await fetch(url.value);
  return res.json();
}, null);
</script>

<template>
  <input type="number" v-model="id" />
  {{ post }}
</template>
