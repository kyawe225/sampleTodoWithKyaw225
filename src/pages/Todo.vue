<template>
    <div class="container py-2 w-100">
        <TodoHeader @save="saveTodo" class="w-100" />
        <TodoBody :todos="todos" />
    </div>
</template>

<script setup lang="ts">
import TodoHeader from "./../components/todo/TodoHeader.vue"
import TodoBody from "./../components/todo/TodoBody.vue"
import { ref, onBeforeMount } from "vue";
import { Todo } from "../model/todo";
import { instance } from "./../webServices/webServices";

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

onBeforeMount(async () => {
    let arr = (await instance.get("/todos")).data;
    todos.value.push(...arr)
})

</script>