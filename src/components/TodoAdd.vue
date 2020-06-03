<template>
  <div>
    <form @submit="addTodo">
      <input v-model="title" type="text" name="todoTitle" placeholder="Add ToDo title" />
      <input type="submit" name="Add" />
    </form>
  </div>
</template>

<script>
export default {
  name: "TodoAdd",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      if (this.title != "") {
        const newTodo = {
          id: Date.now(),

          title: this.title,
          done: false,
          editState: false
        };
        this.title = "";
        this.$emit("add-todo", newTodo);
      }
    }
  }
};
</script>

<style scoped>
</style>