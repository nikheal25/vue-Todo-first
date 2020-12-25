<template>
  <div>
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todoList="todoList" v-on:del-todo="deleteTodo" /></div
></template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Todos,
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
        .then((res) => {
          console.log(res.data); //! Printing response here, or it gives error for Build "Unused variable"
          this.todoList = this.todoList.filter(
            (todoItem) => todoItem.id !== id
          );
        })
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
