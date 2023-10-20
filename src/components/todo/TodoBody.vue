<template>
    <table class="col-12">
        <tbody>
            <tr v-for="item in props.todos">
                <td>
                    <article class="border-bottom p-2 border-bottom-1">
                        <div>{{ item.userId }}</div>
                        <p class="h3">{{ item.title }}</p>
                        <input type="checkbox" v-model="item.completed" :disabled="item.completed" class="form-check-input" />
                    </article>
                </td>
            </tr>
        </tbody>
    </table>
</template>

<script setup lang="ts">
import { defineProps } from 'vue';
import { Todo } from '../../model/todo';
const props = defineProps({
    todos: Array<Todo>
});
</script>