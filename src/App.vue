<script setup lang="ts">
import { ref } from 'vue';
import { useVirtualList } from '@vueuse/core';
import ListItem from './components/ListItem.vue';
const longList = ref(Array.from(Array(100_000).keys()));

// containerProps : 전체 컨테이너 영역
// wrapperProps : list의 바로 부모요소 (여기서는 ul)
const { list, containerProps, wrapperProps } = useVirtualList(longList, {
  itemHeight: 19, //실제 view에서 아이템 높이 (여기서는 li요소)
  overscan: 10, // 그 높이만큼 10개 더 미리 출력
});
</script>

<template>
  <!-- <pre>{{ list }}</pre> -->
  <div class="list-container" v-bind="containerProps">
    <ul v-bind="wrapperProps">
      <ListItem v-for="item in list" :id="item.data" :key="item.data" />
    </ul>
  </div>
</template>

<style>
html,
body,
#app,
.list-container {
  height: 100%;
}
</style>
