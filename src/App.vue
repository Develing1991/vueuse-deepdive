<script setup lang="ts">
import { ref, isRef, toRef, computed } from 'vue';
import { reactify } from '@vueuse/core';
import camelCase from 'lodash/camelCase';
const string = ref('hello_word');
const rCamelCase = reactify(camelCase);
const calmelCaseString = rCamelCase(string);
</script>

<template>
  <input type="text" v-model="string" />
  <br />
  {{ calmelCaseString }}
</template>
