<template>
  <header>
    <h1>ToDo list</h1>
    <slot></slot>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
header {
  text-align: center;
}
</style>