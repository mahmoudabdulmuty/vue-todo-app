<template>
  <ul>
    <li v-for="(todo, index) in todos" :key="index">
      {{ todo }}
      <button @click.prevent="deleteTodo(index)" v-if="todos.length > 0">
        Delete
      </button>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
    },
  },
  methods: {
    deleteTodo(index) {
      this.$emit("delete-todo", index);
    },
  },
};
</script>