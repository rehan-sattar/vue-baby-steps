<template>
  <div class="todo__item" v-bind:class="{'is-completed': todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed" />
      {{todo.name}}
      <!-- we can also use v-bind:on  here  -->
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>


<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>


<style scoped>
.todo__item {
  background-color: #f4f4f4;
  padding: 10px;
  border-bottom: 1px dotted #ccc;
}

.is-completed {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>