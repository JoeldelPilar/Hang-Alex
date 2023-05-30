<template>
	<div class="container">
		<label for="input"> {{ label }}</label>
		<input
			v-bind="$attrs"
			:placeholder="label"
			:value="modelValue"
			@input="emitToParent"
			id="input"
		/>
	</div>
</template>

<script setup lang="ts">
	const emits = defineEmits(['update:modelValue']);

	defineProps({
		label: {
			type: String,
			default: '',
		},
		modelValue: {
			type: [String, Number] || null,
			default: '',
		},
	});

	const emitToParent = (event: Event) => {
		const thisInputValue = (
			event.target as HTMLInputElement
		).value.toLowerCase();
		emits('update:modelValue', thisInputValue);
	};
</script>

<style scoped>
	input {
		margin-block-end: 1rem;
		max-width: 20rem;
	}

	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 1rem;
	}
</style>
