<script>
	import Frontpage from "./Frontpage.svelte";
	import QuestionPage from "./QuestionPage.svelte";
	import ExplanationPage from "./ExplanationPage.svelte";
	import References from "./References.svelte";

	// State variables
	var started = false;
	var dismissQuestionPage = false;
	var displayReferences = false;

</script>

<div id="app">
	<nav>
		<a href="/" on:click|preventDefault={() => {started=false;dismissQuestionPage=false;displayReferences=false;}}>Home</a>
		<a href="/" on:click|preventDefault={() => {started=true;dismissQuestionPage=false;displayReferences=false;}}>Guessing game</a>
		<a href="/" on:click|preventDefault={() => {started=true;dismissQuestionPage=true;displayReferences=false;}}>About the issue</a>
		<a href="/" on:click|preventDefault={() => {started=false;dismissQuestionPage=false;displayReferences=true;}}>References</a>
	</nav>
	{#if displayReferences}
		<References />
	{:else}
		{#if !started}
			<Frontpage bind:buttonClicked={started} />
		{:else}
			{#if dismissQuestionPage}
				<ExplanationPage />
			{:else}
				<QuestionPage bind:dismissQuestionPage={dismissQuestionPage}/>
			{/if}
		{/if}
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