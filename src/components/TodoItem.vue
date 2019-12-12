<template>
  <div>
    <input type="checkbox" v-on:change="todoItemDone" />
    <div class="todoTitleWrap">
      <span v-bind:class="{'done':todo.done}">{{todo.title}}</span>
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
    deleteTodo() {

    }
  }
};
</script>

<style lang="scss" scoped>
</style>