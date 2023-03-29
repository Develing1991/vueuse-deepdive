<script setup>
import { ref, watch } from 'vue';
import { useMagicKeys, whenever } from '@vueuse/core';

const { a_b_c, shift_a, meta_a, ctrl_a, current } = useMagicKeys();
whenever(a_b_c, (pressed) => console.log(pressed));
// const { a, b, c } = useMagicKeys();
// whenever(a, (pressed) => console.log(pressed));
// whenever(b, (pressed) => console.log(pressed));
// whenever(c, (pressed) => console.log(pressed));
</script>

<template>
  {{ current }}
</template>

<style></style>
