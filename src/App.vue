<template>
  <div>
    <Header /><AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todoList="todoList" v-on:del-todo="deleteTodo" /></div
></template>

<script>
import Todos from "./components/Todos";
import Header from "./components/layout/Header";
import AddTodo from "./components/AddTodo";

export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo,
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
    addTodo(newTodo) {
      console.log("addind");
      this.todoList = [...this.todoList, newTodo];
      console.log(this.todoList);
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
