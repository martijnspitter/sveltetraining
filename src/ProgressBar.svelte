<style>
  .progress-container {
    margin: 20px 0;
    border: 1px solid #8f8e8e;
  }
  .progress-bar {
    height: 30px;
    background-color: rgba(77, 199, 55, 1);
  }
</style>

<script>
  export let percentage;
</script>

  <div bp="4@md 12@sm offset-5@md" class="progress-container">
    <div class="progress-bar" style="width: {percentage}%">
      <span class="sr-only">{percentage}%</span>
    </div>
  </div>
