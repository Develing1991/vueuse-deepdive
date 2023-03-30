<script setup lang="ts">
import { ref, computed } from 'vue';
import { logicAnd, logicNot, logicOr } from '@vueuse/math';
const hasBread = ref(true);
const filledWithMeat = ref(true);
const hasTwoSlicesOfBread = ref(true);
const isAHotdog = ref(false);
const isASandWich = computed(() => {
  return logicAnd(
    hasBread,
    filledWithMeat,
    hasTwoSlicesOfBread,
    logicNot(isAHotdog)
  );
});
</script>

<template>
  {{ isASandWich }}
</template>
