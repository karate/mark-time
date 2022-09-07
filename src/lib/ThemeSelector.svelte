<script>
  export let theme;

  let nextTheme;
  const themeToggle = () => {
    theme = nextTheme;
    document.getElementById('settings').getElementsByTagName('div')[0].classList.toggle('hidden');
  }
$: {
  nextTheme = (theme == 'dark')? 'light': 'dark';
}
</script>

<button on:click={themeToggle}>
  Change theme to {nextTheme}
</button>

<style>
</style>
