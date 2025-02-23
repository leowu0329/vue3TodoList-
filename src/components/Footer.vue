<template>
  <div class="flex items-center h-10 pl-1.5 mt-1">
    <label class="inline-block mr-5 cursor-pointer">
      <input type="checkbox" class="relative -top-px align-middle mr-1.5" />
    </label>
    <span> <span>已完成0</span> / 全部2 </span>
    <button
      class="ml-auto mt-1 bg-red-500 hover:bg-red-700 text-white font-bold py-1 px-4 rounded"
    >
      清除已完成任务
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'Footer',
});
</script>
