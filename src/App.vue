<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from "./components/Todos";

export default {
  name: "app",
  components: {
    Todos
  },
  data() {
    return {
      todos: [
        // added defaults here to avoid flash of default data
        {
          id: 1,
          title: 'This is a simple ToDo "app"',
          done: false,
          editState: false
        },
        {
          id: 2,
          title: "You can add, check and delete tasks",
          done: false,
          editState: false
        },
        {
          id: 3,
          title: "These tasks are saved in your browser",
          done: false,
          editState: false
        },
        {
          id: 4,
          title: "You can tab through tasks with keyboard",
          done: false,
          editState: false
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
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  line-height: 1.4;
}
</style>
