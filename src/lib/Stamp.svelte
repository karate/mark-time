<script>
  export let stamp;
  export let stamps;

  const remove = (id) => {
    stamps = stamps.filter(item => item.id !== id);
    stamps = stamps;
  }
</script>

<li on:click={() => remove(stamp.id)}>{stamp.timestamp}</li>

<style>
li {
  list-style: none;
  border-bottom: 1px solid;
  margin-bottom: 5px;
  padding-bottom: 5px;
}
</style>
