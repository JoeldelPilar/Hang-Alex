<script setup lang="ts">
	import { Letter } from '../Letter';

	defineProps({
		letter: Letter,
	});
</script>

<template>
	<span v-if="letter?.show">
		{{ letter?.char }}
	</span>
	<span v-else> {{ ' ' }}</span>
</template>

<style scoped>
	span {
		font-size: 2rem;
		border-bottom: 2px solid yellowgreen;
		min-width: 1rem;
	}
</style>
