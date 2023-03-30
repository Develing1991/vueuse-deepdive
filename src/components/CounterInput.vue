<script lang="ts" setup>
import { useVModel } from '@vueuse/core';
const props = defineProps({
  modelValue: Number,
});
const emit = defineEmits(['update:modelValue']);
const data = useVModel(props, 'modelValue', emit);

// data.value = 10; // emits update:modelValue
</script>

<template>
  <button @click="data--">-</button>
  <input type="number" v-model="data" />
  <button @click="data++">+</button>
</template>

<style>
/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type='number'] {
  -moz-appearance: textfield;
}
</style>
