<script>
  import MarkButton from './lib/Button.svelte'
  import Timestamps from './lib/Timestamps.svelte'
  let stamps = [];
</script>

<main>
  <Timestamps bind:stamps={stamps} />
  <MarkButton bind:stamps={stamps} />
</main>

<style></style>
