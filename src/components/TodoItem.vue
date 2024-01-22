<script setup lang="ts">
    import { computed, ref } from 'vue';
    import TodoIcons from './TodoIcons.vue';
    defineProps(["todo"]);

    const done = ref(false);
    const isTodoDone = computed(() => {
        return done.value === true ? "done" : "";
    }); 
</script>


<template>
	<div class="todo-item" :class="isTodoDone">
		<div class="todo-item-left">
			<input
				class="checkbox"
				type="checkbox"
                v-model="done"
				:id="todo"
			/>
			<label
				:for="todo"
				class="title"
				>{{ todo }}</label
			>
		</div>
		<button
			style="background-color: transparent"
			@click="$emit('deleteTodo', todo)"
		>

        <TodoIcons name="trash" />
		</button>
	</div>
</template>



<style scoped>
	.todo-item {
		display: flex;
		align-items: center;
		justify-content: space-between;
		width: 100%;
		height: 50px;
		border-radius: 10px;
		box-shadow: 0px 4px 16px 0px rgba(0, 0, 0, 0.1);
		padding: 15px;
        transition: 0.3s all;
		/* background: orange; */
	}
	.todo-item-left {
		display: flex;
		align-items: center;
		gap: 15px;
	}
	.title {
		color: #000;
		font-family: "Trebuchet MS";
		font-size: 14px;
		font-weight: 700;
	}

    .done {
        opacity: 0.2;
    }
</style>
