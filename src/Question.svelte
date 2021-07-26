<script>
	export let question
	export let nextQ
	export let incScore

	let isCorrect
	let isAnswered = false

	let answers = question.incorrect_answers.map(answer => {
		return {
			answer,
			correct: false
		}
	})

	let allAnswers = [
		...answers,
		{
			answer: question.correct_answer,
			correct: true
		}
	]
	const shuffle = array => {
		array.sort(() => Math.random() - 0.5)
	}

	const checkQuestion = correct => {
		if (!isAnswered) {
			isAnswered = true
			isCorrect = correct
			if (correct) {
				incScore()
			}
		}
	}

	shuffle(allAnswers)

	console.log(`conlog: `, allAnswers)
</script>

<hr />
<h3>{@html question.question}</h3>
<h4>
	{#if isAnswered}
		{#if isCorrect}
			<span style="color: green;"> Right</span>
		{:else}
			<span style="color: red;"> WRONG. </span>
		{/if}
	{:else}
		<span> Select.</span>
	{/if}
</h4>

{#each allAnswers as answer}
	<button on:click={() => checkQuestion(answer.correct)}>{@html answer.answer}</button>
{/each}
{#if isAnswered}
	<div>
		<button on:click={nextQ}>Next ></button>
	</div>
{/if}
