<template>
  <div class="flex justify-center items-center min-h-screen bg-gray-100">
    <div
      class="w-[600px] p-2.5 border border-gray-300 rounded-lg bg-white shadow-sm"
    >
      <Header :addTodo="addTodo" />
      <List :todos="todos" :deleteTodo="deleteTodo" :updateTodo="updateTodo" />
      <Footer
        :todos="todos"
        :checkAll="checkAll"
        :clearAllCompletedTodos="clearAllCompletedTodos"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, reactive, toRefs, watch } from 'vue';
import Header from './components/Header.vue';
import List from './components/List.vue';
import Footer from './components/Footer.vue';
import { Todo } from './types/todo';
import { saveTodos, readTodos } from './utils/localStorageUtils';

export default defineComponent({
  name: 'App',
  components: {
    Header,
    List,
    Footer,
  },
  setup() {
    // const state = reactive<{ todos: Todo[] }>({
    //   todos: [
    //     { id: 1, title: '吃飯', isCompleted: false },
    //     { id: 2, title: '散步', isCompleted: true },
    //     { id: 3, title: '看電影', isCompleted: false },
    //   ],
    // });
    const state = reactive<{ todos: Todo[] }>({
      todos: [],
    });

    onMounted(() => {
      setTimeout(() => {
        state.todos = readTodos();
      }, 100);
    });

    const addTodo = (todo: Todo) => {
      state.todos.unshift(todo);
    };

    const deleteTodo = (index: number) => {
      state.todos.splice(index, 1);
    };

    const updateTodo = (todo: Todo, isCompleted: boolean) => {
      todo.isCompleted = isCompleted;
      console.log(todo);
    };

    const checkAll = (isCompleted: boolean) => {
      state.todos.forEach((todo) => {
        todo.isCompleted = isCompleted;
      });
    };

    const clearAllCompletedTodos = () => {
      state.todos = state.todos.filter((todo) => !todo.isCompleted);
    };

    watch(() => state.todos, saveTodos, { deep: true });

    return {
      ...toRefs(state),
      addTodo,
      deleteTodo,
      updateTodo,
      checkAll,
      clearAllCompletedTodos,
    };
  },
});
</script>
