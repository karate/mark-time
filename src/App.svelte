<script>
  import Event from './lib/Event.svelte'
  import CreateEventButton from './lib/CreateEventButton.svelte'
  import Settings from './lib/Settings.svelte'

  import {onMount} from "svelte";

  let user_pref = {
    'theme': 'light',
    'events': [],
    'default': true,
  };

  if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
    user_pref.theme = 'dark';
  }

  onMount(() => {
    // Load settings from local storage
    user_pref = JSON.parse(localStorage.getItem('preferences')) || user_pref;
    user_pref.default = false;
  });

  $: {
    // Update local storage when data change
    if (user_pref.default !== true) {
      localStorage.setItem('preferences', JSON.stringify(user_pref));
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
  <Settings bind:data={user_pref}/>
  <a class="github" target="_blank" href="https://github.com/karate/mark-time">GitHub</a>
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

  main {
    background-color: #f1f1f1;
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
