<script setup lang="ts">
	import { ref } from 'vue';
	import BaseInput from './Base/BaseInput.vue';
	import LetterButton from './LetterButton.vue';
	import LetterSpan from './LetterSpan.vue';
	import { Letter, alphabetLetters } from '../Letter';

	const solutionWord = ref('');

	const solutionLetters = ref<Letter[]>([]);

	const gameStarted = ref(false);

	const startGame = () => {
		for (var i = 0; i < solutionWord.value.length; i++) {
			const letter = new Letter(solutionWord.value[i]);
			// solutionLetters.push(letter);
			solutionLetters.value = [...solutionLetters.value, letter];
		}
		gameStarted.value = true;
		solutionWord.value = '';
	};

	const checkLetter = (letter: string) => {
		solutionLetters.value.map((letterObject) => {
			if (letter === letterObject.char) {
				letterObject.show = true;
				return letterObject;
			}
			return letterObject;
		});
		console.log(solutionLetters.value);
	};
</script>

<template>
	<main>
		<form
			@submit.prevent="startGame"
			v-if="!gameStarted"
		>
			<BaseInput
				label="Skriv ditt ord"
				type="text"
				v-model="solutionWord"
			/>
			<button>Lets Hang!</button>
		</form>

		<div class="letterspan__container">
			<LetterSpan
				v-for="(letter, index) in solutionLetters"
				:key="index"
				>{{ letter }}</LetterSpan
			>
		</div>

		<div
			class="button__container"
			v-if="gameStarted"
		>
			<LetterButton
				v-for="char in alphabetLetters"
				:key="char"
				@clickedLetter="checkLetter"
			>
				{{ char }}
			</LetterButton>
		</div>
	</main>
</template>

<style scoped>
	.button__container {
		display: flex;
		gap: 0.5rem;
	}

	.letterspan__container {
		display: flex;
		gap: 0.5rem;
		justify-content: center;
	}
</style>
