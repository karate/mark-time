<script>
  export let event;

  const increment = () => {
    const now = new Date();
    event.stamps.push({
      'id': event.stamps.length,
      'timestamp': now.toLocaleString()
    });
    event = event;
  }
</script>

<button on:click={increment}>
  Mark the time
</button>

<style>
button {
  width: 100%;
  font-size: 1.3rem;
  padding: 10px;
}
</style>
