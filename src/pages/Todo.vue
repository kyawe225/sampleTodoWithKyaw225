<template>
    <TodoHeader @save="saveTodo" />
    <TodoBody :todos="todos" />
</template>

<script setup lang="ts">
import TodoHeader from "./../components/todo/TodoHeader.vue"
import TodoBody from "./../components/todo/TodoBody.vue"
import { ref, onBeforeMount } from "vue";
import { Todo } from "../model/todo";

const todos = ref<Todo[]>([]);

const saveTodo = (item: string) => {
    let todo: Todo = {
        userId: 1,
        completed: true,
        id: todos.value.length + 1,
        title: item
    }
    todos.value.push(todo);
}

onBeforeMount(() => {
    let arr = [
        {
            userId: 1,
            completed: false,
            id: todos.value.length + 1,
            title: 'a'
        },
        {
            userId: 2,
            completed: true,
            id: todos.value.length + 1,
            title: 'b'
        },
        {
            userId: 3,
            completed: true,
            id: todos.value.length + 1,
            title: 'c'
        }
    ]
    todos.value.push(...arr)
})

</script>