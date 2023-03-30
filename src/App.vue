<script setup lang="ts">
import { ref } from 'vue';
import { useRefHistory, useDebouncedRefHistory } from '@vueuse/core';
const newTodo = ref('');
const todos = ref([]);

const { history, undo, redo } = useRefHistory(todos, {
  deep: true,
  capacity: 10, // 히스토리 용량 최대 10
});
</script>

<template>
  <input type="text" v-model="newTodo" placeholder="New Todo" />
  <button
    @click="
      todos.unshift(newTodo);
      newTodo = '';
    "
  >
    Create Todo
  </button>
  <button @click="undo">Undo</button>
  <button @click="redo">Redo</button>
  <ul>
    <li v-for="todo in todos" :key="todo">{{ todo }}</li>
  </ul>
  <br />
  <pre>{{ history }}</pre>
</template>
