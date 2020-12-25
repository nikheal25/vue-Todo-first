<template>
  <div>
    <Header /><AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todoList="todoList" v-on:del-todo="deleteTodo" /></div
></template>

<script>
import Todos from "./components/Todos";
import Header from "./components/layout/Header";
import AddTodo from "./components/AddTodo";
import axios from "axios";

export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo,
  },
  data() {
    return {
      todoList: [],
    };
  },
  methods: {
    deleteTodo(id) {
      console.log(id);
      //this.todoList = this.todoList.filter((todoItem) => todoItem.id !== id);
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(
          (res) =>
            (this.todoList = this.todoList.filter(
              (todoItem) => todoItem.id !== id
            ))
        )
        .catch((err) => console.log(err));
    },
    addTodo(newTodo) {
      console.log("addind");

      const { title, completed } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed,
        })
        .then((res) => (this.todoList = [...this.todoList, res.data]))
        .catch((err) => console.log(err));

      //this.todoList = [...this.todoList, newTodo];
      console.log(this.todoList);
    },
  },

  created() {
    console.log("Created call");
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then((res) => (this.todoList = res.data))
      .catch((err) => console.log(err));
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
