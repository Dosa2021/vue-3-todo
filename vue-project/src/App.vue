<script setup>
import { ref } from 'vue';

const todos = [
  'Buy Milk',
  'Go to Gym',
  'Study JavaScript'
]

// const newTodo = 'new todo';
const newTodo = ref('new todo');

function addTodo(e) {
  e.preventDefault();
  alert(newTodo.value);
}

function handleInput(e) {
  newTodo.value = e.target.value
}
</script>

<template>
  <div class="container">
    <h1>Todos</h1>
    <ul>
      <li v-for="todo in todos">{{ todo }}</li>
    </ul>
    <form @submit="addTodo">
      <input type="text" :value="newTodo" @input="handleInput">
      <button>Add</button>
    </form>
  </div>
</template>

<style scoped>
.container {
  width: 400px;
  margin: 0 auto;
}

h1 {
  font-size: 20px;
  border-bottom: 1px solid;
  padding: 8px;
}
</style>