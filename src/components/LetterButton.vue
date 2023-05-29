<script setup lang="ts">
	import { ref } from 'vue';

	const handleClick = (event: Event) => {
		isDisabled.value = true;
		const click = (event.target as HTMLButtonElement).innerHTML;
		emits('clickedLetter', click);
	};

	const isDisabled = ref(false);

	const emits = defineEmits(['clickedLetter']);
</script>

<template>
	<button
		@click="handleClick"
		:disabled="isDisabled"
	>
		<slot></slot>
	</button>
</template>

<style scoped></style>
