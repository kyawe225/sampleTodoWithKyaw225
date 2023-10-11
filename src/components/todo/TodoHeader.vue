<template>
    <form @submit.prevent="SaveTodo">
        <div>
            <input type="text" v-model="todo" />
        </div>
        <input type="submit" value="save" />
    </form>
</template>

<script setup lang="ts">
import { ref,defineEmits } from 'vue';

const save=defineEmits(["save"]);

const todo = ref("");

const SaveTodo=()=>{
    save("save",todo.value);
}

</script>