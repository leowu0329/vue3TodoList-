<template>
  <li class="list-none h-9 leading-9 px-2 border-b border-gray-300">
    <label class="float-left cursor-pointer">
      <input type="checkbox" class="align-middle mr-1.5 relative -top-px" />
      <span>xxxxx</span>
    </label>
    <button
      class="float-right hidden mt-0.75 bg-red-500 text-white px-2 py-1 rounded"
    >
      删除
    </button>
  </li>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'Item',
});
</script>

<style>
/* 如果需要额外的自定义样式，可以在这里添加 */
</style>
