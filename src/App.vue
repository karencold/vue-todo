<template>
  <div id="app">
    <Header />
    <TodoAdd v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from "./components/layouts/Header";
import Todos from "./components/Todos";
import TodoAdd from "./components/TodoAdd";

export default {
  name: "app",
  components: {
    Todos,
    Header,
    TodoAdd
  },
  data() {
    return {
      todos: [
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
      // delete todo item
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
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
