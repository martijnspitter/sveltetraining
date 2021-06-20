<script>
	import HowTo from './HowTo.svelte';
	import Timer from './Timer.svelte';

	let audio;

	function timerEnds() {
		audio.play()
	}
</script>

<style>
	h1, h3 {
		text-align: center;
	}
</style>

<h1>Handwashing App</h1>
<Timer on:end={timerEnds}/>

<HowTo />
<h3>Source</h3>
<audio bind:this={audio}>
	<source src="sound.wav" />
	<track kind="captions">
</audio>
