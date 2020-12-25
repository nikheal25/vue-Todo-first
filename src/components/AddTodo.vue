<template>
  <div>
    <form @submit="addTodo">
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add Todo...."
      /><input type="submit" value="Submit" />
    </form>
  </div>
</template>

<script>
// import uuid from "uuid";
// import { v4 as uuidv4 } from "uuid";
export default {
  name: "AddTodo",
  data() {
    return { title: "" };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();

      const newTodo = {
        // id: uuidv4(),
        title: this.title,
        completed: false,
      };
      //SEND IT TO PARENT
      console.log("hrere");
      this.$emit("add-todo", newTodo);
      this.title = ""; // Clears the title
    },
  },
};
</script>

<style></style>
