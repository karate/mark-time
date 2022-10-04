<script>
  export let stamp;
  export let stamps;
  export let idx;

  const remove = (id) => {
    stamps = stamps.filter(item => item.id !== id);
    stamps = stamps;
  }

  const relativeDiff = (diff) => {
    if (diff == null) return null;
    if (diff < 60) {
      return diff + ' seconds';
    }
    else if (diff < 3600) {
      let hours = parseInt(diff / 3600);
      if (hours < 10) hours = '0' + hours;
      let minutes = Math.round(diff % 3600 / 60);
      if (minutes < 10) minutes = '0' + minutes;
      return hours + ':' + minutes;
    }
    else if (diff < 86400) {
      let days = parseInt(diff / 86400);
      let hours = Math.round(diff % 86400 / 3600);
      return days + ' days, ' + hours + ' hours';
    }
  }

  const d = new Date(stamp.timestamp);
  var diff = relativeDiff(parseInt(stamp.diff / 1000));
  if (stamp.diff == null) diff = null;

</script>

<li on:click={() => remove(stamp.id)}>
  {idx+1}) 
  {d.toLocaleString('en-GB')} 
  {#if diff}
    (+{diff})
  {/if}
</li>

<style>
li {
  list-style: none;
  border-bottom: 1px solid;
  margin-bottom: 5px;
  padding-bottom: 5px;
}
</style>
