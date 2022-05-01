<template>
  <input type="text" placeholder="add todo" v-model="todo" />
  <button @click.prevent="addTodo">add</button>
</template>

<script>
export default {
  data() {
    return {
      todo: "",
    };
  },
  emits: ["add-todo"],
  methods: {
    addTodo() {
      this.$emit("add-todo", this.todo);
      this.todo = "";
    },
  },
};
</script>