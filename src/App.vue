<script setup lang="ts">
import { refAutoReset } from '@vueuse/core';
const showAlert = refAutoReset(false, 3000);
showAlert.value = true;
</script>

<template>
  <transition appear>
    <div v-if="showAlert" class="alert">Your post has been saved</div>
  </transition>
  <button @click="showAlert = true">Show Alert</button>
</template>

<style>
.v-enter-active,
.v-leave-active {
  transition: all 0.2s ease;
}

.v-enter-from,
.v-leave-to {
  transform: translateY(-10px);
  opacity: 0;
}

.alert {
  -webkit-text-size-adjust: 100%;
  tab-size: 4;
  font-family: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont,
    Segoe UI, Roboto, Helvetica Neue, Arial, Noto Sans, sans-serif,
    apple color emoji, segoe ui emoji, Segoe UI Symbol, noto color emoji;
  -webkit-tap-highlight-color: transparent;
  --su: 158 64% 52%;
  font-size: 1rem;
  line-height: 1.75;
  box-sizing: border-box;
  border-width: 0;
  border-style: solid;
  border-color: #e5e7eb;
  display: flex;
  width: 100%;
  gap: 1rem;
  padding: 1rem;
  border-radius: 10px;
  align-items: center;
  --tw-bg-opacity: 1;
  background-color: hsl(var(--su) / var(--tw-bg-opacity));
}

.alert::before {
  content: '';
  width: 20px;
  height: 20px;
  background: url(/icon.svg);
}
</style>
