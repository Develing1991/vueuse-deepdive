<script setup lang="ts">
import { ref } from 'vue';
import { useInfiniteScroll } from '@vueuse/core';

const el = ref<HTMLElement>(null);
const data = ref([]);
const total = ref(0);

useInfiniteScroll(el, loadData, { distance: 10 });

loadData();

async function loadData() {
  if (data.value.length !== 0 && data.value.length >= total.value) return;
  const res = await fetch(
    `https://dummyjson.com/products/?limit=10&skip=${data.value.length}`
  );
  const d = await res.json();
  total.value = d.total;
  data.value = data.value.concat(d.products);
}
</script>

<template>
  <div ref="el" class="el">
    <div v-for="item in data" class="card">
      <img :src="item.thumbnail" alt="" />
      <h3>{{ item.title }}</h3>
      <p>{{ item.description }}</p>
    </div>
  </div>
</template>

<style>
html,
body,
#app {
  height: 100%;
}
.el {
  height: 100%;
  overflow-y: scroll;
}
.card {
  margin: 30px 10px;
  box-shadow: 0 0 3px 4px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  padding: 20px;
}
img {
  border-radius: 10px;
  display: block;
  width: 100%;
}
</style>
