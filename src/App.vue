<script setup>
import { ref, watch } from 'vue';
import { useBattery } from '@vueuse/core';

const battery = useBattery();
</script>

<template>
  {{ battery }}
</template>

<style></style>
