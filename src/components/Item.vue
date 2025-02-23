<template>
  <li class="list-none h-9 leading-9 px-2 border-b border-gray-300">
    <label class="float-left cursor-pointer">
      <input type="checkbox" class="align-middle mr-1.5 relative -top-px" />
      <span>{{ todo?.title }}</span>
    </label>
    <button
      class="float-right hidden mt-0.75 bg-red-500 text-white px-2 py-1 rounded"
      style="display: none"
    >
      删除
    </button>
  </li>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import { Todo } from '../types/todo';

export default defineComponent({
  name: 'Item',
  props: {
    todo: {
      type: Object as PropType<Todo>,
      required: true,
    },
  },
});
</script>
