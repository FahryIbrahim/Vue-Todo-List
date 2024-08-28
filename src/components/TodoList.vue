<template>
  <div class="todo-container w-96 max-w-lg mx-auto p-6 bg-white dark:bg-gray-900 text-gray-900 dark:text-gray-100 rounded-lg shadow-lg">
    <h1 class="text-center text-2xl font-semibold mb-4 text-black">Todo List</h1>
    <input
      type="text"
      v-model="newTodo"
      @keyup.enter="addTodo"
      placeholder="Add a new todo"
      class="w-full text-black p-3 mb-4 border border-gray-300 dark:border-gray-700 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:text-black"
    />
    <ul class="list-none p-0">
      <li
        v-for="(todo, index) in todos"
        :key="index"
        class="flex justify-between items-center p-4 mb-2 bg-gray-100 dark:bg-gray-800 rounded-lg border border-gray-200 dark:border-gray-700"
      >
        <span
          :class="{ 'line-through text-gray-500': todo.completed }"
          class="cursor-pointer"
          @click="toggleComplete(index)"
        >
          {{ todo.text }}
        </span>
        <button
          @click="deleteTodo(index)"
          class="bg-red-500 text-white py-2 px-4 rounded-lg hover:bg-red-600 transition-colors"
        >
          Delete
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({ text: this.newTodo.trim(), completed: false });
        this.newTodo = "";
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    toggleComplete(index) {
      this.todos[index].completed = !this.todos[index].completed;
    }
  }
};
</script>

<style scoped>
.todo-container {
  background-color: #ffffff;
}
</style>
