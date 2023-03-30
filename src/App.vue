<script setup lang="ts">
import { ref, computed } from 'vue';
import { useNow, useDateFormat } from '@vueuse/core';
const now = useDateFormat(useNow(), 'YYYY-MM-DD HH:mm:ss:SSS');
</script>

<template>
  {{ now }}
</template>
