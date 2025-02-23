<template>
  <ul class="list-none p-0 border border-gray-300 rounded-md">
    <Item />
  </ul>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Item from './Item.vue';

export default defineComponent({
  name: 'List',
  components: {
    Item,
  },
});
</script>

<style>
/* 如果需要保留一些自定义样式，可以在这里添加 */
</style>
