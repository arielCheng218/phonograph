<script>
	export var buttonClicked = false;

	const toggleButtonClickedTrue = () => {
		buttonClicked = true;
	};
	
</script>

<div id="frontpage">
	<h1>Can you tell the difference?</h1>
	<p>You will hear two pieces: one of which is human-composed lofi, and the other is <a href="https://github.com/zacharykatsnelson/Lofi-Hip-Hop-Generator"> AI-composed lofi</a>. Try and guess which is which.</p>
	<p>Disclaimer: drum tracks for all pieces have been composed by humans.</p>
	<button on:click={toggleButtonClickedTrue}>Start</button>
	<canvas id="canvasElmId"></canvas>
</div>

<style>
	#frontpage {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 80vh;
		text-align: center;
		padding-left: 48px;
		padding-right: 48px;
	}
	p {
		max-width: 500px;
	}
</style>