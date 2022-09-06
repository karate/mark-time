<script>
  export let events;

  const create = () => {
    let eventName = prompt("Enter event name");
    if (eventName) {
      events.push({'id': events.length, 'name':eventName, 'stamps': []})
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
