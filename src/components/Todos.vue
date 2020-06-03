<template>
  <ul class="todoList">
    <li class="todoItem" :key="todo.id" v-for="todo in todos">
      <TodoItem
        :todo="todo"
        @edit-todo="$emit('edit-todo', todo.id)"
        @toggle-done="$emit('toggle-done', todo.id)"
        @del-todo="$emit('del-todo', todo.id)"
        @todo-blur="$emit('todo-blur', todo.id)"
      />
    </li>
  </ul>
</template>

<script>
import TodoItem from "./TodoItem";
export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: ["todos"]
};
</script>

<style scoped>
ul {
  padding: 0;
  margin: 10px 0;
}
li {
  list-style: none;
}
</style>