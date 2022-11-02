<script>
  export let events;

  const create = () => {
    let eventName = prompt("Enter event name");
    if (eventName) {
      let NextEventId = 0;
      if (events.length > 0) {
        NextEventId = events.at(-1).id + 1;
      }
      events.push({'id': NextEventId, 'name':eventName, 'stamps': []})
      events = events;
    }
  }
</script>

<button on:click={create}>
  Create event
</button>

<style>
button {
  display: block;
  margin: auto;
  font-size: inherit;
}
</style>
