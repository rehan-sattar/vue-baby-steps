<template>
  <div id="app">
    <Header />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Header from "./layout/Header";

export default {
  name: "App",
  components: {
    Header,
    Todos
  },
  data() {
    return {
      todos: [
        {
          id: "1",
          name: "go to bank",
          completed: false
        },
        {
          id: "2",
          name: "Shopping Center",
          completed: false
        },
        {
          id: "3",
          name: "Study Maths",
          completed: false
        },
        {
          id: "4",
          name: "Sleep at night!",
          completed: true
        }
      ]
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
