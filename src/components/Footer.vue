<template>
  <div class="flex items-center h-10 pl-1.5 mt-1">
    <label class="inline-block mr-5 cursor-pointer">
      <input
        type="checkbox"
        class="relative -top-px align-middle mr-1.5"
        v-model="isCheckAll"
      />
    </label>
    <span>
      <span>已完成{{ count }}</span> / 全部{{ todos.length }}
    </span>
    <button
      class="ml-auto mt-1 bg-red-500 hover:bg-red-700 text-white font-bold py-1 px-4 rounded"
    >
      清除已完成任务
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { Todo } from '../types/todo';
import { computed } from '@vue/reactivity';
export default defineComponent({
  name: 'Footer',
  props: {
    todos: {
      type: Array as () => Todo[],
      required: true,
    },
    checkAll: {
      type: Function,
      required: true,
    },
  },
  setup(props) {
    const count = computed(() => {
      return props.todos.reduce(
        (pre, todo, index) => pre + (todo.isCompleted ? 1 : 0),
        0,
      );
    });

    const isCheckAll = computed({
      get() {
        return count.value > 0 && props.todos.length === count.value;
      },
      set(val) {
        props.checkAll(val);
      },
    });
    return {
      count,
      isCheckAll,
    };
  },
});
</script>
