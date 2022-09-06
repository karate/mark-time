<script>
  import Category from './lib/Category.svelte'
  import CreateCategoryButton from './lib/CreateCategoryButton.svelte'
  import ThemeSelector from './lib/ThemeSelector.svelte'

  import {onMount} from "svelte";
  import { writable } from 'svelte-local-storage-store'
  import { get } from 'svelte/store'

  let user_pref = {
    'theme': 'dark',
    'categories': [],
    'default': true,
  };
  export const preferences = writable('preferences', user_pref);

  onMount(() => {
    // Load settings from local storage
    user_pref = get(preferences);
    console.log('Loading preferences', user_pref);
    user_pref.default = false;
  });

  $: {
    // Update local storage when data change
    if (user_pref.default !== true) {
      console.log('Saving preferences');
      console.log(user_pref);
      preferences.set(user_pref);
    }
  }
</script>

<main class={user_pref.theme}>
  <CreateCategoryButton bind:categories={user_pref.categories}/>
  <div class="categories">
    {#each user_pref.categories as category}
      <Category bind:category={category} bind:categories={user_pref.categories} />
    {/each}
  </div>
  <ThemeSelector bind:theme={user_pref.theme}/>
</main>

<style>
  :global(body, html, #app){
    margin: 0;
    height: 100%;
    font-size: 16px;
    color: #1e1e1e;
  }

  main {
    height: 100%;
  }

  main .categories {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }

  main.dark {
    background-color: #323232;
  }

</style>
