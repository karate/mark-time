<script>
  import Category from './lib/Category.svelte'
  import CreateCategoryButton from './lib/CreateCategoryButton.svelte'
  let categories = [];
</script>

<main>
  <CreateCategoryButton bind:categories={categories}/>
  {#each categories as category}
    <Category bind:category={category} bind:categories={categories} />
  {/each}
</main>

<style></style>
