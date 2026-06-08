<script setup>
import { ref } from 'vue';

const emit = defineEmits(['addTodoEvent']);
const newTodo = ref('');

function handleSubmit() {
    emit('addTodoEvent', newTodo.value)
}
</script>

<template >
    <form @submit.prevent="handleSubmit">
        <input type="text" v-model="newTodo">
      <button>Add</button>
    </form>
</template>

<style scoped>
form {
    display: flex;
    gap: 4px;
}

input {
    flex: 1;
    padding: 4px;
}
</style>