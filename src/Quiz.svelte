<svelte:options tag="webc-quiz" />

<script>
	import { onMount } from "svelte"
	import Question from "./Question.svelte"
	let activeQ = 0
	let score = 0
	let quiz = getQuiz()
	// let quiz

	async function getQuiz() {
		const res = await fetch("https://opentdb.com/api.php?amount=10&category=15&type=multiple")
		const quiz = await res.json()
		console.log(`conlog: `, await quiz)
		return quiz
	}

	const nextQ = () => {
		activeQ = activeQ + 1
	}

	const reset = () => {
		quiz = getQuiz()
		score = 0
	}

	const incScore = () => {
		score = score + 1
	}
</script>

<div>
	<button on:click={reset}>Get Quiz</button>
	<h3>Score: {score}</h3>
	<h4>Q: {activeQ + 1}</h4>

	{#await quiz}
		Loading...
	{:then data}
		{#each data.results as question, idx}
			{#if idx === activeQ}
				<Question {incScore} {nextQ} {question} />
			{/if}
		{/each}
	{/await}
</div>
