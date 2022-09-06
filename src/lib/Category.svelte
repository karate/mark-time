<script>
  import MarkButton from './MarkButton.svelte'
  import Stamp from './Stamp.svelte'
  export let category;
  export let categories;

  const remove = (id) => {
    console.log("Deleting Category", id);
    categories = categories.filter(item => item.id !== id);
    categories = categories;
  }
</script>

<section>
  <h1 on:click={() => remove(category.id)}>{category.name}</h1>
  <MarkButton bind:category={category} />
  <ul>
    {#each category.stamps as stamp}
      <Stamp stamp={stamp} bind:stamps={category.stamps}/> 
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
