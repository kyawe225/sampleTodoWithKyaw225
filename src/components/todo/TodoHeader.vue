<template>
    <div class="w-100">
        <div class="alert" :class="success ? 'alert-success' : 'alert-danger'" v-if="message != ''">
            {{ message }}
        </div>

        <form @submit.prevent="SaveTodo" class="d-flex col-12 px-4 gap-2">
            <input type="text" class="form-control" v-model="todo" />
            <input type="submit" value="save" class="btn btn-primary " />
        </form>
    </div>
</template>

<script setup lang="ts">
import { ref, defineEmits } from 'vue';

const success=ref(false);

const save = defineEmits(["save"]);

const todo = ref("");

const message = ref("");

const SaveTodo = () => {
    if (todo.value.trim() != "") {
        save("save", todo.value);
        message.value = "save Successfully";
        success.value=true;
        todo.value = "";
        setTimeout(()=> message.value="" , 1000);
    } else {
        message.value = "Todo Has No Value";
        success.value=false;
    }
}

</script>