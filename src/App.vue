<template>
  <div id="app" class="bg-gray-900 min-h-screen flex items-center justify-center p-4">
    <TodoList />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    TodoList
  }
};
</script>

<style>
body {
  @apply bg-gray-900 text-white font-sans;
}
</style>
