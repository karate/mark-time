<script>
  export let category;

  const increment = () => {
    const now = new Date();
    category.stamps.push({
      'id': category.stamps.length,
      'timestamp': now.toLocaleString()
    });
    category = category;
  }
</script>

<button on:click={increment}>
  Mark the time
</button>
