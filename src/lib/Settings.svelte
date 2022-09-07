<script>
  export let data;
  import ThemeSelector from './ThemeSelector.svelte'
  import ImportExport from './ImportExport.svelte'

  const toggle = () => {
    console.log(document.getElementById('settings').getElementsByTagName('div'));
    document.getElementById('settings').getElementsByTagName('div')[0].classList.toggle('hidden');
  }
</script>

<div id="settings">
  <div class="hidden">
    <ImportExport bind:data={data} />
    <ThemeSelector bind:theme={data.theme} />
  </div>
  <button on:click={toggle}>Settings</button>
</div>

<style>
  div.hidden {
    display: none;
  }

  div#settings {
    display: inline-block;
    position: fixed;
    bottom: 20px;
    left: 20px;
  }

  :global(div#settings > div > button) {
    display: block;
    margin: 5px;
  }
</style>
