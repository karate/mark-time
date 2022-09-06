<script>
  import Category from './lib/Category.svelte'
  import CreateCategoryButton from './lib/CreateCategoryButton.svelte'

  import {onMount} from "svelte";
  import { writable } from 'svelte-local-storage-store'
  import { get } from 'svelte/store'

  let categories = [];
  export const preferences = writable('categories', categories);

  onMount(() => {
    // Load settings from local storage
    categories = get(preferences);
  });

  $: {
    // Update local storage when data change
    if (categories.length > 0) {
      preferences.set(categories)
    }
  }
</script>

<main>
  <CreateCategoryButton bind:categories={categories}/>
  <div class="categories">
    {#each categories as category}
      <Category bind:category={category} bind:categories={categories} />
    {/each}
  </div>
</main>

<style>
  main .categories {
    display: flex;
    flex-wrap: wrap;
  }
</style>
