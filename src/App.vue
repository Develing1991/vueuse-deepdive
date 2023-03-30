<script setup lang="ts">
import { ref } from 'vue';
import { useTimeout } from '@vueuse/core';
const { ready, start, stop, isPending } = useTimeout(5000, { controls: true });
</script>

<template>
  {{ ready }}
  {{ isPending }}
  <Transition appear>
    <div class="alert" v-if="isPending">
      You post has benn saved
      <button @click="stop">X</button>
    </div>
  </Transition>
  <button @click="start">start</button>
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
