<script setup>
import { reactive } from 'vue';
import TodoList from './components/TodoList.vue';
import TodoAddForm from './components/TodoAddForm.vue';

const todos = reactive([
  {
    id: crypto.randomUUID(),
    title: 'Item 0',
    isCompleted: false
  },
  {
    id: crypto.randomUUID(),
    title: 'Item 1',
    isCompleted: true
  },
  {
    id: crypto.randomUUID(),
    title: 'Item 2',
    isCompleted: false
  },
]);

function addTodo(newTodo) {
  todos.push({
    id: crypto.randomUUID(),
    title: newTodo,
    isCompleted: false
  })
}

function toggleIsCompleted(todo) {
  const index = todos.findIndex((element) => {
    return element.id === todo.id
  })
  todos[index].isCompleted = !todos[index].isCompleted;
}
</script>

<template>
  <div class="container">
    <h1>Todos</h1>
    <TodoList :todos="todos" @checkTodoEvent="toggleIsCompleted" />
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