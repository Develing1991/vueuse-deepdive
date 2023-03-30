<script setup lang="ts">
import { ref, watchEffect } from 'vue';
import { useDisplayMedia } from '@vueuse/core';
const video = ref();
const { stream, enabled } = useDisplayMedia();
// useUserMedia - camera
// useMediaControls - video player
watchEffect(() => {
  if (video.value) {
    video.value.srcObject = stream.value;
  }
});
</script>

<template>
  <button @click="enabled = !enabled">Start Screen Share</button>
  <video ref="video" muted autoplay controls width="800" />
</template>
