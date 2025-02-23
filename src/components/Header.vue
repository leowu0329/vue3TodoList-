<template>
  <div class="todo-header">
    <input
      type="text"
      v-model="title"
      @keyup.enter="add"
      placeholder="请输入你的任务名称，按回车键确认"
      class="w-[560px] h-7 text-sm border border-gray-300 rounded-md px-2 py-1 focus:outline-none focus:border-blue-500 focus:ring-1 focus:ring-blue-500"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
export default defineComponent({
  name: 'Header',
  props: {
    addTodo: {
      type: Function,
      required: true,
    },
  },
  setup(props) {
    const title = ref('');
    const add = () => {
      const text = title.value;
      if (!text.trim()) return;
      const todo = {
        id: Date.now(),
        title: text,
        isCompleted: false,
      };
      props.addTodo(todo);
      title.value = '';
    };
    return {
      title,
      add,
    };
  },
});
</script>
