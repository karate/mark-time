<script>
  export let stamps;

  const increment = () => {
    const now = new Date();
    stamps.push({
      'id': stamps.length,
      'timestamp': now.toLocaleString()
    });
    stamps = stamps;
  }
</script>

<button on:click={increment}>
  Mark the time
</button>
