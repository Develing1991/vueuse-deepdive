<script setup lang="ts">
import { ref, computed } from 'vue';
import { useWindowFocus } from '@vueuse/core';
const focused = useWindowFocus();
</script>

<template>{{ focused }}</template>
