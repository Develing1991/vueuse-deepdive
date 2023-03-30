<script setup lang="ts">
import { ref, computed } from 'vue';
import { useWindowSize } from '@vueuse/core';
const { width, height } = useWindowSize();
</script>

<template>{{ width }} x {{ height }}</template>
