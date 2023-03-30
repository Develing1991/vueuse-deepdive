<script setup>
import { ref, watch } from 'vue';
import { useNetwork } from '@vueuse/core';

const network = useNetwork();
</script>

<template>
  {{ network }}
</template>

<style></style>
