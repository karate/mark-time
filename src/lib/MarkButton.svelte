<script>
  export let event;

  let diff = null;

  const mark = () => {
    const now = new Date();
    if (event.stamps.length >= 1) {
      let last_stamp = new Date(event.stamps[event.stamps.length - 1].timestamp);
      diff = now - last_stamp;
    }

    var nextStampId = 0;
    if (event.stamps.length > 0) {
      nextStampId = event.stamps.at(-1).id + 1;
    }

    event.stamps.push({
      'id': nextStampId,
      'timestamp': now.getTime(),
      'diff': diff
    });
    event = event;
  }
</script>

<button on:click={mark}>
  Mark the time
</button>

<style>
button {
  width: 100%;
  font-size: 1.3rem;
  padding: 10px;
}
</style>
