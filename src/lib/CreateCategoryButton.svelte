<script>
  export let categories;

  const create = () => {
    let categoryName = prompt("Enter Category name");
    if (categoryName) {
      categories.push({'id': categories.length, 'name':categoryName, 'stamps': []})
      categories = categories;
    }
  }
</script>

<button on:click={create}>
  Create Category
</button>

<style>
button {
  display: block;
  margin: auto;
  font-size: inherit;
}
</style>
