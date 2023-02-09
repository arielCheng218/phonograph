<script>
	import Frontpage from "./Frontpage.svelte";
	import QuestionPage from "./QuestionPage.svelte";
	import ExplanationPage from "./ExplanationPage.svelte";
	import References from "./References.svelte";

	// State variables
	var started = false;

</script>

<div id="app">
	<nav>
		<a href="/" on:click|preventDefault={() => {started=false}}>Home</a>
		<a href="/" on:click|preventDefault={() => {started=true}}>Guessing game</a>
		<a href="https://docs.google.com/document/d/1UiIqPue2XlpBlGzB__PrJjKKlq8FE1Odgfdu73HWKNc/edit">About the issue</a>
		<a href="https://www.kaggle.com/arielcheng218/generating-lofi-music-with-rnns/edit">Kaggle Notebook</a>
		<a href="https://docs.google.com/document/d/1oe9B1c4kJe71XXYFfw5c5opxjY8xoq9YYKRviTq58ho/edit">References</a>
	</nav>
		{#if !started}
			<Frontpage bind:buttonClicked={started} />
		{:else}
			<QuestionPage />
		{/if}
</div>

<style>
	nav {
		display: flex;
		flex-direction: row;
		gap: 16px;
		padding: 32px;
	}
	a {
		text-decoration: none;
		color: black;
		font-weight: bold;
	}
</style>