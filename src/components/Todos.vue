<template>
  <div>
    <h1>Todo List</h1>

    <div v-for="todo in todoList" v-bind:key="todo.id">
      <!-- <h3>{{ todo.title }}</h3> -->
      <!-- todo.completed.sync="todo.completed" -->
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";
export default {
  name: "Todos",

  components: {
    TodoItem,
  },
  props: ["todoList"],
};
</script>

<style scoped></style>
