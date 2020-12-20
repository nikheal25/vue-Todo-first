<template>
  <div>
    <h1>Todo List</h1>

    <div v-for="todo in todoList" v-bind:key="todo.id">
      <h3>{{ todo.title }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todos",
  props: ["todoList"],
};
</script>

<style scoped></style>
