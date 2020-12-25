<template>
  <div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
    <p>
      <input type="checkbox" v-on:change="markComplete" /> {{ todo.title }}
      <button class="del" @click="$emit('del-todo', todo.id)">Delete</button>
    </p>
  </div></template
>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  data() {
    return {
      todoLocal: this.todo,
    };
  },
  methods: {
    markComplete() {
      this.todoLocal.completed = !this.todoLocal.completed;
    },
  },
};
</script>

<style scoped>
.todo-item {
  background: rgb(223, 220, 220);
}
.is-complete {
  text-decoration: line-through;
}
.del {
  color: red;
}
</style>
