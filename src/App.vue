<script setup lang="ts">
import { ref, computed } from 'vue';
import { useFetch } from '@vueuse/core';
const id = ref(1);
const url = computed(() => {
  return `https://jsonplaceholder.typicode.com/todos/${id.value}`;
});
const { isFetching, data, error } = useFetch(url, {
  refetch: true,
});
</script>

<template>
  <input type="text" v-model="id" />
  <div v-if="error">{{ error }}</div>
  <div v-else-if="isFetching">Loading...</div>
  <pre v-else>
  {{ data }}
  </pre>
</template>
