<script setup>
import { ref, watch } from 'vue';
import { useOnline } from '@vueuse/core';

const online = useOnline();
</script>

<template>
  {{ online }}
</template>

<style></style>
