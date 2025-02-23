<template>
  <div class="flex justify-center items-center min-h-screen bg-gray-100">
    <div
      class="w-[600px] p-2.5 border border-gray-300 rounded-lg bg-white shadow-sm"
    >
      <Header :addTodo="addTodo" />
      <List :todos="todos" :deleteTodo="deleteTodo" />
      <Footer />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue';
import Header from './components/Header.vue';
import List from './components/List.vue';
import Footer from './components/Footer.vue';
import { Todo } from './types/todo';

export default defineComponent({
  name: 'App',
  components: {
    Header,
    List,
    Footer,
  },
  setup() {
    const state = reactive<{ todos: Todo[] }>({
      todos: [
        { id: 1, title: '吃飯', isCompleted: false },
        { id: 2, title: '散步', isCompleted: true },
        { id: 3, title: '看電影', isCompleted: false },
      ],
    });

    const addTodo = (todo: Todo) => {
      state.todos.unshift(todo);
    };

    const deleteTodo = (index: number) => {
      state.todos.splice(index, 1);
    };

    return {
      ...toRefs(state),
      addTodo,
      deleteTodo,
    };
  },
});
</script>
