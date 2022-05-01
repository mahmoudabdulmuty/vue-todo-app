<template>
  <h1>Todo App</h1>
  <add-todo @add-todo="addTodo"></add-todo>
  <display-todos :todos="todos" @delete-todo="deleteTodo"></display-todos>
</template>

<script>
import AddTodo from "./components/AddTodo";
import displayTodos from "./components/displayTodos";
export default {
  name: "App",
  components: { AddTodo, displayTodos },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
    },
    deleteTodo(index) {
      this.todos = this.todos.filter((todo, i) => i !== index);
    },
  },
};
</script>

<style>
</style>
