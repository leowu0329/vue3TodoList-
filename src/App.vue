<template>
  <div class="flex justify-center items-center min-h-screen bg-gray-100">
    <div
      class="w-[600px] p-2.5 border border-gray-300 rounded-lg bg-white shadow-sm"
    >
      <Header />
      <List />
      <Footer />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Header from './components/Header.vue';
import List from './components/List.vue';
import Footer from './components/Footer.vue';
export default defineComponent({
  name: 'App',
  components: {
    Header,
    List,
    Footer,
  },
});
</script>
