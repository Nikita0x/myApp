<script setup lang="ts">
	import TodoIcons from "./TodoIcons.vue";
	import { store } from "@/store/TodosStore.vue";

	defineProps(["item", "index"]);

	function handleToggle(todoIndex: number) {
		store.value.forEach((item, index) => {
			if (todoIndex === index) {
				item.done = !item.done;
			}
		});
	}

	function handleDelete(todoIndex: number) {
		store.value.splice(todoIndex, 1);
	}
</script>

<template>
	<div
		class="todo-item"
		:class="{ done: item.done }"
	>
		<div class="todo-item-left">
			<input
				class="checkbox"
				type="checkbox"
				:checked="item.done"
				@change="handleToggle(index)"
			/>
			<label
				@click="handleToggle(index)"
				class="title"
            >
                {{ item.title }}
			</label>

			<div
				:class="['custom-checkbox',{ 'custom-checkbox-checked': item.done }]"
				@click="handleToggle(index)"
			>
				<TodoIcons name="tick" v-show="item.done" />
			</div>
		</div>
		<button
			style="background-color: transparent"
			@click="handleDelete(index)"
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
	}
	.todo-item-left {
		position: relative;
		display: flex;
		align-items: center;
		gap: 15px;
	}
	.todo-item-left input {
		position: absolute;
		opacity: 0;
		cursor: pointer;
		height: 0;
		width: 0;
	}
	.custom-checkbox {
		position: absolute;
		display: flex;
		align-items: center;
		justify-content: center;
		cursor: pointer;
		width: 25px;
		height: 25px;
		border-radius: 3px;
		border: 2px solid black;
	}
	.custom-checkbox-checked {
		position: absolute;
		background-color: #00000033;
		width: 25px;
		height: 25px;
		border-radius: 3px;
		border: 1px solid transparent;
	}
	.title {
		color: #000;
		font-family: "Trebuchet MS";
		font-size: 14px;
		font-weight: 700;
		max-width: 290px;
		padding-left: 38px;
		max-height: 50px;
		overflow: auto;
	}

	.done {
		opacity: 0.2;
	}
</style>
