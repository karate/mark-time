<script>
  export let categories;

  const increment = () => {
    let categoryName = prompt("Enter Category name");
    categories.push({'name':categoryName, 'stamps': []})
    categories = categories;
  }
</script>

<button on:click={increment}>
  Create Category
</button>
