<template>
  <div>
    <input type="checkbox" v-on:change="todoItemDone" />
    <div class="todoTitleWrap">
      <span v-bind:class="{'done':todo.done}" class="todoTitle">{{todo.title}}</span>
    </div>
    <button name="delete" class="deleteItem" v-on:click="$emit('del-todo', todo.id)">x</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    todoItemDone() {
      this.todo.done = !this.todo.done;
    },
    deleteTodo() {}
  }
};
</script>

<style scoped>
.todoItem div {
  display: flex;
}
.todoTitle {
  margin-left: 5px;
}
.deleteItem {
  margin-left: 5px;
}
.done {
  text-decoration: line-through;
}
</style>