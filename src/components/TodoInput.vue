<script setup lang="ts">
    import TodoIcons from './TodoIcons.vue';
    import { ref } from 'vue';
    import { store } from '@/store/TodosStore.vue';
    const newTodo = ref({title: "", done: false})

    function handleAddNewTodo() {
        store.value.push(newTodo.value)
        newTodo.value = {title: "", done: false}
    }
</script>



<template>
    <div class="todo-container">
        <input 
            :value = "newTodo.title"
            @input="event => newTodo.title = (event.target as HTMLInputElement).value"
            @keyup.enter="handleAddNewTodo"
            class="input"
            placeholder="Enter your new ToDo..."
            type="text"
        >
        <button 
            @click="handleAddNewTodo"
            class="add-button"
        >
            <TodoIcons name="add"/>
        </button>
    </div>
</template>




<style scoped>
    .todo-container {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 15px;
        width: 100%;
        height: 50px;
        border-radius: 10px;
        background: #F0F0F0;
        transition: all 0.3s;
    }

    .todo-container:focus-within {
        outline: 1px rgba(0, 0, 0, 0.447) dashed;
    }

    .input {
        background-color: transparent;
        border: none;
        outline: none;
        color: black;
        font-family: "Trebuchet MS";
        font-size: 14px;
        font-weight: 700;
        width: 90%;
    }

    .input::placeholder {
        color: rgba(0, 0, 0, 0.20);
        font-family: "Trebuchet MS";
        font-size: 14px;
        font-weight: 700;
    }

    .add-button {
        width: 25px;
        height: 25px;
        background-color: transparent;
    }

</style>