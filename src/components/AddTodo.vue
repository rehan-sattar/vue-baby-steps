<template>
  <form @submit="addTodo">
    <input type="text" placeholder="Add item" name="title" v-model="title" />
    <input type="submit" value="Submit" class="btn" />
  </form>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      if (this.title.length === 0) return;
      const newTodo = {
        title: this.title,
        completed: false
      };
      this.$emit("add-todo", newTodo);
      this.title = "";
    }
  }
};
</script>


<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
  border-radius: 0;
  outline: none;
}
input[type="submit"] {
  flex: 2;
}
</style>
