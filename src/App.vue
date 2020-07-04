<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import axios from "axios";

import Todos from "./components/Todos";
import Header from "./layout/Header";
import AddTodo from "./components/AddTodo";

const URL = "https://jsonplaceholder.typicode.com/todos";

export default {
  name: "App",
  components: {
    Header,
    AddTodo,
    Todos
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`${URL}/${id}`)
        .then(() => (this.todos = this.todos.filter(todo => todo.id !== id)))
        .catch(err => console.log("Error: ", err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post(URL, {
          title,
          completed
        })
        .then(res => (this.todos = this.todos.concat(res.data)))
        .catch(err => console.log("ERROR: ", err));
    }
  },
  created() {
    axios
      .get(`${URL}?_limit=5`)
      .then(res => (this.todos = res.data))
      .catch(err => console.log("ERROR:", err));
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

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
