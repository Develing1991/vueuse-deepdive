<script setup lang="ts">
import { ref } from 'vue';
import { useBase64 } from '@vueuse/core';
const string = ref('');
const image = ref('');
const { base64 } = useBase64(string);
const { base64: base64Image } = useBase64(image);
</script>

<template>
  <input type="text" v-model="string" />
  <input
    type="file"
    accept="image/png, image/jpeg"
    @change="image = $event.target.files[0]"
  />
  <br />
  {{ base64 }}
  <img v-if="image" :src="base64Image" width="200" />
</template>
