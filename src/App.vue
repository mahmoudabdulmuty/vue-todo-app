<template>
  <h1>Todo app</h1>
  <form @submit.prevent="addNewTodo">
    <h2>Add A New Todo</h2>
    <input
      v-if="state.todos.length"
      type="search"
      v-model="searchQuery"
      placeholder="Search Todos"
    />
    <input type="text" v-model="state.newTodo" placeholder="add a new todo" />
    <button>add</button>
    <ul v-if="filteredTodos.length">
      <li v-for="todo in filteredTodos" :key="todo.id">
        <h3
          @click="toggleDone(todo)"
          :style="{
            textDecoration: `${todo.done ? 'line-through' : 'none'}`,
          }"
        >
          {{ todo.content }}
        </h3>
        <button @click="deleteTodo(todo.id)">Delete Todo</button>
      </li>
    </ul>
    <h3 v-if="!filteredTodos.length">No todos</h3>
  </form>
</template>

<script setup>
import { computed, reactive, ref } from 'vue';

const state = reactive({
  newTodo: '',
  todos: [],
});

const searchQuery = ref('');

const addNewTodo = () => {
  if (state.newTodo) {
    state.todos.push({
      content: state.newTodo,
      done: false,
      id: Math.random(),
    });
  }
  state.newTodo = '';
};

const toggleDone = (todo) => {
  todo.done = !todo.done;
};

const deleteTodo = (id) => {
  state.todos = state.todos.filter((todo) => todo.id !== id);
};

const filteredTodos = computed(() => {
  if (searchQuery.value) {
    return state.todos.filter((todo) =>
      todo.content.toLowerCase().includes(searchQuery.value.toLowerCase())
    );
  } else {
    return state.todos;
  }
});
</script>

<style></style>
