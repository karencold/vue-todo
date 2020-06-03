<template>
  <div class="grid">
    <input type="checkbox" @change="$emit('toggle-done', todo.id)" />
    <div class="todoTitleWrap">
      <textarea
        @input="resize"
        @focus="resize"
        v-show="todo.editState"
        ref="todoInput"
        type="text"
        v-model="todo.title"
        @blur="$emit('todo-blur', todo.id)"
        @keypress.enter="$emit('todo-blur', todo.id)"
      />
      <span
        v-show="!todo.editState"
        @click="triggerEdit"
        :class="{'done':todo.done}"
        class="todoTitle"
      >{{todo.title}}</span>
    </div>
    <button name="delete" class="deleteItem" @click="$emit('del-todo', todo.id)">x</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],

  methods: {
    triggerEdit() {
      this.$emit("edit-todo", this.todo.id);
      // hack for waiting for edit state to trigger
      setTimeout(() => {
        this.$refs.todoInput.focus();
      }, 0);
    },
    resize(e) {
      e.target.style.height = "";
      window.console.log(e.target.scrollHeight);
      e.target.style.height = `${e.target.scrollHeight}px`;
    }
  }
};
</script>

<style scoped>
textarea {
  width: 100%;
  border: none;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  line-height: 1.4;
  font-size: 16px;
  padding: 0;
  resize: none;
  word-wrap: break-word;
}
span {
  font-size: 16px;
}
.todoTitleWrap {
  margin-left: 5px;
}
.deleteItem {
  margin-left: 5px;
}
.done {
  text-decoration: line-through;
}
.grid {
  display: grid;
  grid-template-columns: 20px 1fr 30px;
  align-items: center;
}
</style>