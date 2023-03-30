<script setup lang="ts">
import { ref } from 'vue';
import { useVModel } from '@vueuse/core';
import CounterInput from './components/CounterInput.vue';
const number = ref(0);
</script>

<template>
  <CounterInput v-model="number" />
  <br />
  {{ number }}
</template>
