<script setup lang="ts">
	defineProps(["name"]);
</script>

<template>
	<svg
		v-if="name === 'trash'"
		xmlns="http://www.w3.org/2000/svg"
		width="16"
		height="16"
	>
		<path
			d="M13.5 3h-3v-.75A1.25 1.25 0 0 0 9.25 1h-2.5A1.25 1.25 0 0 0 5.5 2.25V3h-3a.5.5 0 1 0 0 1h.531l.594 9.529c.044.839.688 1.471 1.5 1.471h5.75c.817 0 1.447-.618 1.5-1.469L12.969 4h.531a.5.5 0 0 0 0-1ZM6.018 13H6a.5.5 0 0 1-.5-.482l-.25-7a.5.5 0 1 1 1-.036l.25 7a.5.5 0 0 1-.482.518Zm2.482-.5a.5.5 0 0 1-1 0v-7a.5.5 0 1 1 1 0v7Zm1-9.5h-3v-.75A.247.247 0 0 1 6.75 2h2.5a.247.247 0 0 1 .25.25V3Zm1 9.518A.5.5 0 0 1 10 13h-.018a.5.5 0 0 1-.482-.518l.25-7a.5.5 0 0 1 1 .036l-.25 7Z"
			fill-opacity=".3"
		/>
	</svg>

	<svg
		v-else-if="name === 'add'"
		xmlns="http://www.w3.org/2000/svg"
		width="25"
		height="25"
		fill="none"
	>
		<path
			d="M12.5 2.344C6.9 2.344 2.344 6.9 2.344 12.5c0 5.6 4.556 10.156 10.156 10.156 5.6 0 10.156-4.556 10.156-10.156 0-5.6-4.556-10.156-10.156-10.156Zm4.688 10.937H13.28v3.906H11.72v-3.906H7.813V11.72h3.906V7.813h1.562v3.906h3.906v1.562Z"
			fill="#000"
			fill-opacity=".5"
		/>
	</svg>

	<svg
        v-else-if="name === 'tick'"
		width="12"
		height="10"
		fill="none"
		xmlns="http://www.w3.org/2000/svg"
	>
		<path
			d="M11 1 4 9 1 6"
			stroke="#fff"
			stroke-width="2"
			stroke-linecap="round"
			stroke-linejoin="round"
		/>
	</svg>
</template>
