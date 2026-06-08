<script setup>
import { reactive, ref } from 'vue';
import TodoList from './components/TodoList.vue';

// const todos = [
//   'Buy Milk',
//   'Go to Gym',
//   'Study JavaScript'
// ]
// const todos = reactive([
//   'Buy Milk',
//   'Go to Gym',
//   'Study JavaScript'
// ]);
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

// const newTodo = 'new todo';
const newTodo = ref('');

function addTodo(e) {
  if (newTodo.value.trim() === '') {
    return;
  }

  e.preventDefault();
  // alert(newTodo.value);
  todos.push({
    id: crypto.randomUUID(),
    title: newTodo.value
  })
  newTodo.value = '';
}

function handleInput(e) {
  newTodo.value = e.target.value
}
</script>

<template>
  <div class="container">
    <h1>Todos</h1>

    <TodoList :todos="todos"/>

    <form @submit="addTodo">
      <!-- <input type="text" :value="newTodo" @input="handleInput"> -->

       <!-- Note: v-model -->
      <input type="text" v-model="newTodo">
      <button>Add</button>
    </form>
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