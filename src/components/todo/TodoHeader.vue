<template>
    <div>
        {{ message }}
    </div>
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

const message=ref("");

const SaveTodo=()=>{
    if(todo.value.trim() != ""){
        save("save",todo.value);
        message.value="";
        todo.value="";
    }else{
        message.value="Todo Has No Value";
    }
}

</script>