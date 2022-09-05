<script>
  import MarkButton from './Button.svelte'
  import Stamp from './Stamp.svelte'
  export let category;
  export let categories;

  const remove = (name) => {
    console.log("Deleting Category", name);
    categories = categories.filter(item => item.name !== name);
    categories = categories;
  }
</script>

<section>
  <h3 on:click={() => remove(category.name)}>{category.name}</h3>
  <MarkButton bind:category={category} />
  {#each category.stamps as stamp}
    <Stamp stamp={stamp} bind:stamps={category.stamps}/> 
  {/each}
</section>
