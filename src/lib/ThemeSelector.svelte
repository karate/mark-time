<script>
  export let theme;

  let nextTheme;
  const themeToggle = () => {
    theme = nextTheme;
  }
$: {
  nextTheme = (theme == 'dark')? 'light': 'dark';
}
</script>

<button on:click={themeToggle}>
  Change theme to {nextTheme}
</button>

<style>
  button {
    position: fixed;
    bottom: 10px;
    left: 10px;
  }
</style>
