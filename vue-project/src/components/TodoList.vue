<script setup>
// TODO: どうやってデバッグするの？
const props = defineProps({
    todos: Array,
 });
const emit = defineEmits('checkTodoEvent')

function handleClick(todo) {
    emit('checkTodoEvent', todo)
}
</script>

<template>
    <ul>
      <li v-for="todo in todos">
        <label>
            <input
                type="checkbox"
                :checked="todo.isCompleted"
                @click="handleClick(todo)"
            >
            {{ todo.title }}
        </label>
        <button>delete</button>
    </li>
    </ul>
</template>

<style scoped>
    ul {
        margin: 0;
        padding: 0;
        list-style: none;
    }
    li + li {
        margin-top: 1px;
    }
    li {
        display: flex;
        gap: 4px;
    }
    label:has(:checked) {
        color: #ccc;
        text-decoration: line-through;
    }
    button {
        margin-left: auto;
    }
</style>