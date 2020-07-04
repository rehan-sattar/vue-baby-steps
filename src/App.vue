<template>
  <div id="app">
    <Todos v-bind:todos="todos" />
  </div>
</template>

<script>
import Todos from "./components/Todos";

export default {
  name: "App",
  components: {
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
