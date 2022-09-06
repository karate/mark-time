<script>
  import MarkButton from './MarkButton.svelte'
  import Stamp from './Stamp.svelte'
  export let event;
  export let events;

  const remove = (id) => {
    events = events.filter(item => item.id !== id);
    events = events;
  }
</script>

<section>
  <h1 on:click={() => remove(event.id)}>{event.name}</h1>
  <MarkButton bind:event={event} />
  <ul>
    {#each event.stamps as stamp}
      <Stamp stamp={stamp} bind:stamps={event.stamps}/>
    {/each}
  </ul>
</section>

<style>
  section {
    min-width: 250px;
    background-color: #2196f3;
    padding: 1rem;
    margin: 1rem;
    border-radius: 10px;
    text-align: center;
  }

  :global(main.dark section) {
    background-color: #095895;
    color: white;
  }

  h1 {
    font-size: 2rem;
    font-family: sans-serif;
    margin: 0 0 12px;
  }

  ul {
    margin: 20px 0;
    padding: 0;
    font-family: monospace;
  }
</style>
