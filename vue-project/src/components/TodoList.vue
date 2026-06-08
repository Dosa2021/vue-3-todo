<script setup>
const props = defineProps({
    todos: Array,
 });
</script>

<template>
    <ul>
      <li v-for="todo in todos">{{ todo.title }}</li>
    </ul>
</template>