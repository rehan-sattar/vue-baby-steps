<template>
  <div class="todo__item" v-bind:class="{'is-completed': todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed" />
      {{todo.name}}
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
</style>