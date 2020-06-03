<template>
  <div id="app">
    <Header>
      <TodoAdd v-on:add-todo="addTodo" />
    </Header>
    <Todos
      v-bind:todos="todos"
      @del-todo="deleteTodo"
      @edit-todo="editStateInit"
      @toggle-done="doneToggle"
      @todo-blur="editStateDelete"
    />
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
          title: "You can add, check, edit and delete tasks",
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
    },
    doneToggle(id) {
      this.todos = this.todos.map(todo => {
        todo.id === id ? (todo.done = !todo.done) : null;
        return todo;
      });
    },
    editStateInit(id) {
      this.todos = this.todos.map(todo => {
        todo.id === id ? (todo.editState = true) : null;
        return todo;
      });
    },
    editStateDelete(id) {
      this.todos = this.todos.map(todo => {
        todo.id === id ? (todo.editState = false) : null;
        return todo;
      });
    }
  }
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
#app {
  box-sizing: border-box;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  line-height: 1.4;
  width: 60%;
  min-width: 320px;
  margin: auto;
  padding: 0 10px;
}
</style>
