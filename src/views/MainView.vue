<script setup lang="ts">
	import TodoItem from "@/components/TodoItem.vue";
	import TodoInput from "@/components/TodoInput.vue";
	import { store } from "@/store/TodosStore.vue";
</script>

<template>
	<div class="container">
		<div class="content">
			<div class="header">
				<img
					src="../../public/Logo.svg"
					alt="Logo"
				/>
			</div>

			<div class="body">
				<TransitionGroup name="animation">
					<TodoItem
						v-for="(item, index) in store"
						:key="index"
						:item="item"
						:index="index"
					/>
				</TransitionGroup>
			</div>

			<div class="footer">
				<TodoInput />
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

	.content {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		width: 430px;
		height: 100%;
		max-height: 932px;
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
	}
</style>
