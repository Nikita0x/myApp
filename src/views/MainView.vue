<script setup lang="ts">
    import { ref } from 'vue'; 
    import TodoItem from '@/components/TodoItem.vue';
    import TodoInput from "@/components/TodoInput.vue"

    const storedTodos = localStorage.getItem("todos");
    const todos = ref(storedTodos ? JSON.parse(storedTodos) : [])

    const msg = ref('')

    function handleDelete(id: string) {
        todos.value.forEach((item: any, index: number) => {
            if(id === item) {
                todos.value.splice(index, 1)
            }
        })
        localStorage.setItem("todos", JSON.stringify(todos.value))
    }

    function handleAddTodo(value: string) {
        console.log(value, "has been added!")
        todos.value.push(value)
        msg.value = ""
        localStorage.setItem("todos", JSON.stringify(todos.value))
    }

</script>

<template>
    <div class="container">
        <div class="content">

            <div class="header">
                <img src="../../public/Logo.svg" alt="Logo">
            </div>
            
            <div class="body">
                <TransitionGroup name="animation">
                    <TodoItem v-for="(todo, index) in todos" :key="index" :todo="todo" :id="index"  @delete-todo="handleDelete" />
                </TransitionGroup>
            </div>

            <div class="footer">
                <TodoInput v-model="msg" @add-todo="handleAddTodo" />
            </div>

        </div>
    </div>
</template>




<style scoped>
        .animation-move,
        .animation-enter-active,
        .animation-leave-active {
            transition: all 0.5s ease;
            scale: 1;
        }
        .animation-enter-from,
        .animation-leave-to {
            opacity: 0;
            scale: 0;
        }
        .animation-leave-active {
            position: absolute;
            }
    .container {
        background-color: rgb(30, 25, 25);
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

    .content{
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        width: 430px;
        height: 100%;
        padding-left: 40px;
        padding-right: 40px;
        padding-bottom: 30px;
        padding-top: 30px;
        background-color: whitesmoke;
    }

    .header {
        display: flex;
        align-items: center;
        justify-content: center;
        padding-top: 45px;
        filter: drop-shadow(0px 4px 16px rgba(0, 25, 75, 0.15));
        /* background-color: red; */
    }

    .body {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        gap: 10px;

        padding-top: 10px;
        padding-bottom: 10px;
        max-height: 600px;
        overflow: auto;

        /* background-color: orange; */
    }
</style>
