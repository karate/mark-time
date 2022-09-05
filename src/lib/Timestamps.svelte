<script>
  import Stamp from './Stamp.svelte'
  export let stamps;
</script>

<ul>
{#each stamps as stamp}
  <Stamp stamp={stamp} bind:stamps={stamps}/> 
{/each}
</ul>
