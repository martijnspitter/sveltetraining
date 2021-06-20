<script>
  import ProgressBar from './ProgressBar.svelte';
  import {createEventDispatcher} from 'svelte';

  const totalSeconds = 20;
  let secondsLeft = totalSeconds;
  let isRunning = false;
  $: progres = (totalSeconds - secondsLeft) / totalSeconds * 100;
  const dispatch = createEventDispatcher()
  function startTimer() {
  isRunning = true;
  const timer = setInterval(() => {
    secondsLeft -= 1;
    if (secondsLeft === 0) {
      clearInterval(timer);
      isRunning = false;
      dispatch('end')
      setTimeout(() => {
        secondsLeft = totalSeconds;        
      }, 1000);
    }
  }, 1000);
}
  
</script>

<style>
 h2 {
   margin: 0;
 }
 .start {
   background-color: rgb(154, 73, 73);
   width: 100%;
   margin: 15px 0;
 }
 .start[disabled] {
  background-color: #8f8e8e;
  cursor: not-allowed;
 }
</style>

<div bp="grid">
  <h2 bp="4@md 12@sm offset-5@md">Seconds left: {secondsLeft}</h2>
  <ProgressBar percentage={progres}/>
  
  <button bp="4@md 12@sm offset-5@md" disabled={isRunning} on:click={startTimer} class="start">Start</button>
</div>