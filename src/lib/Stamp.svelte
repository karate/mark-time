<script>
  export let stamp;
  export let stamps;

  const remove = (id) => {
    console.log("Deleting ", id);
    stamps = stamps.filter(item => item.id !== id);
    stamps = stamps;
  }
</script>

<li on:click={() => remove(stamp.id)}>{stamp.timestamp}</li>
