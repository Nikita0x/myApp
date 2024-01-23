<script lang="ts">
    import { ref, watchEffect } from 'vue';

    const store = ref([
        {title: "Create a todo app", done: false},
    ])

    // Try to retrieve todos from local storage during component creation
    const storedTodos = localStorage.getItem("todos");
    if (storedTodos) {
        store.value = JSON.parse(storedTodos);
    }

    watchEffect(() => {
        localStorage.setItem("todos", JSON.stringify(store.value));
        console.log("Your todos were saved to local storage.");
    });

    export { store }
</script>