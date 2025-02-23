<template>
  <li
    @mouseenter="mouseHandler(true)"
    @mouseleave="mouseHandler(false)"
    :class="[
      'flex',
      'items-center',
      'justify-between',
      'h-9',
      'px-2',
      'border-b',
      'border-gray-300',
      'last:border-b-0',
      bgColor,
      myColor,
    ]"
  >
    <label class="float-left cursor-pointer">
      <input type="checkbox" class="align-middle mr-1.5 relative -top-px" />
      <span>{{ todo?.title }}</span>
    </label>
    <button
      :class="['btn', 'btn-danger', isShow ? 'block' : 'hidden']"
      class="float-right hidden mt-0.75 bg-red-500 text-white px-2 py-1 rounded"
      style="display: none"
    >
      删除
    </button>
  </li>
</template>

<script lang="ts">
import { defineComponent, PropType, ref } from 'vue';
import { Todo } from '../types/todo';

export default defineComponent({
  name: 'Item',
  props: {
    todo: {
      type: Object as PropType<Todo>,
      required: true,
    },
  },
  setup() {
    const bgColor = ref('bg-white');
    const myColor = ref('text-black');
    const isShow = ref(false);

    const mouseHandler = (flag: boolean) => {
      if (flag) {
        bgColor.value = 'bg-sky-300/100';
        myColor.value = 'text-pink-500';
        isShow.value = true;
      } else {
        bgColor.value = 'bg-white';
        myColor.value = 'text-black';
        isShow.value = false;
      }
    };

    return {
      mouseHandler,
      bgColor,
      myColor,
      isShow,
    };
  },
});
</script>
