<script>
  import Event from './lib/Event.svelte'
  import CreateEventButton from './lib/CreateEventButton.svelte'
  import ThemeSelector from './lib/ThemeSelector.svelte'

  import {onMount} from "svelte";
  import { writable } from 'svelte-local-storage-store'
  import { get } from 'svelte/store'

  let user_pref = {
    'theme': 'dark',
    'events': [],
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
  <CreateEventButton bind:events={user_pref.events}/>
  <div class="events">
    {#each user_pref.events as event}
      <Event bind:event={event} bind:events={user_pref.events} />
    {/each}
  </div>
  <ThemeSelector bind:theme={user_pref.theme}/>
  <a class="github" target="_blank" href="https://github.com/karate/mark-time">Github</a>
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

  main .events {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }

  main.dark {
    background-color: #323232;
  }

  .github {
      position: fixed;
      bottom: 10px;
      right: 10px;
  }

  main.dark .github {
    color: white;
  }
</style>
