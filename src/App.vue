<template>
  <div>
    <Todos v-bind:todoList="todoList" v-on:del-todo="deleteTodo" /></div
></template>

<script>
import Todos from "./components/Todos";
export default {
  name: "App",
  components: {
    Todos,
  },
  data() {
    return {
      todoList: [
        {
          id: 1,
          title: "Do homework",
          completed: false,
        },
        {
          id: 2,
          title: "Do excercise",
          completed: false,
        },
        {
          id: 3,
          title: "Cook lunch",
          completed: true,
        },
      ],
    };
  },
  methods: {
    deleteTodo(id) {
      console.log(id);
      this.todoList = this.todoList.filter((todoItem) => todoItem.id !== id);
    },
  },
};
</script>

<style>
* {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
