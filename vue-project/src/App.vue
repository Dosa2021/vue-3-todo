<script setup>
import { reactive } from 'vue';
import TodoList from './components/TodoList.vue';
import TodoAddForm from './components/TodoAddForm.vue';

const todos = reactive([
  {
    id: crypto.randomUUID(),
    title: 'Item 0'
  },
  {
    id: crypto.randomUUID(),
    title: 'Item 1'
  },
  {
    id: crypto.randomUUID(),
    title: 'Item 2'
  },
]);

function addTodo(newTodo) {
  console.log('addtodo')
  console.log(newTodo)
}

</script>

<template>
  <div class="container">
    <h1>Todos</h1>

    <TodoList :todos="todos"/>

    <TodoAddForm @addTodoEvent="addTodo"/>

  </div>
  <img src="/mei_1.jpg" alt="">
</template>

<style scoped>
.container {
  margin: 0 auto;
  padding-bottom: 10px;
  width: 500px;
}

h1 {
  font-size: 20px;
  border-bottom: 1px solid;
  padding: 8px;
}

img {
  width: 100%;
}
</style>