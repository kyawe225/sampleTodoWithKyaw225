<template>
    <table>
        <tbody>
            <tr v-for="item in props.todos">
                <td>
                    <article>
                        <div>{{ item.userId }}</div>
                        <p>{{ item.title }}</p>
                        <input type="checkbox" v-model="item.completed" :disabled="item.completed" />
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