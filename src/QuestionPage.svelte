<script>

	export var dismissQuestionPage;
	var displayOptionsPage = false;

	var index = 0;
	var numCorrect = 0;
	var aiPiecePath = `/assets/ai_${index+1}.mp3`;
	var humanPiecePath = `/assets/human_${index+1}.mp3`;
	var audioTrack1 = aiPiecePath;
	var audioTrack2 = humanPiecePath;
	var answer = "track-1-checkbox";
	var checkbox1 = false;
	var checkbox2 = false;

	const handleCheckboxClick = (e) => {
		// handle whether the guess was correct
		if (e.target.id === answer) {
			alert('Correct!');
			checkbox1 = false;
			checkbox2 = false;
			numCorrect++;
		} else {
			alert('Wrong!');
			checkbox1 = false;
			checkbox2 = false;
		}
		if (index < 2) {
			index = index + 1;
			const x = Math.random();
			if (x > 0.5) {
				audioTrack1 = `/assets/ai_${index+1}.mp3`;
				audioTrack2 = `/assets/human_${index+1}.mp3`;
				answer = "track-1-checkbox";
			} else {
				audioTrack2 = `/assets/human_${index+1}.mp3`;
				audioTrack1 = `/assets/ai_${index+1}.mp3`;
				answer = "track-2-checkbox";
			}
		} else {
			displayOptionsPage = true;
		}
	};

	const playAgain = () => {
		index = 0;
		displayOptionsPage = false;
	};

</script>

<div class="question-page">
	{#if !displayOptionsPage}
		<h2>Which track is composed by AI?</h2>
		<h3>Question {index+1}/3</h3>
		<div class="row">
			<input id="track-1-checkbox" type="checkbox" bind:checked={checkbox1} on:click|preventDefault={handleCheckboxClick}/>
			<audio class="audio" controls src={audioTrack1} />
		</div>
		<div class="row">
			<input id="track-2-checkbox" type="checkbox" bind:checked={checkbox2} on:click|preventDefault={handleCheckboxClick}/>
			<audio class="audio" controls src={audioTrack2} />
		</div>
	{:else}
		<h1>You got {numCorrect}/3 right!</h1>
		<button on:click={playAgain}>Play Again</button>
	{/if}
</div>

<style>
	.question-page {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 80vh;
		text-align: center;
		padding-left: 48px;
		padding-right: 48px;
		gap: 16px;
	}
	.row {
		display: flex;
		gap: 8px;
	}
</style>