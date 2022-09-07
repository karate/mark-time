<script>
  export let data;

  var exportElement;
  var exportInput;

  const exportSettings = () => {
    exportElement = document.getElementsByClassName('export')[0];
    exportInput = exportElement.getElementsByTagName('input')[0];
    exportInput.value = JSON.stringify(data);
    exportElement.classList.remove('hidden');
    exportInput.focus();
    exportInput.select();
  }

  const importSettings = () => {
    let userData = prompt("Paste encoded data below");
    if (userData) {
      data = JSON.parse(userData);
    }
  }

  const dismiss = () => {
    exportElement.classList.add('hidden');
  }

  const copy = () => {
    navigator.clipboard.writeText(JSON.stringify(data))
    .then(function() {
    }, function() {
      console.error("Unable to write to clipboard. :-(");
    });
    dismiss();
  }
</script>

<button on:click={exportSettings}>Export</button>
  <section class="export hidden">
    <h3>Please copy the following string</h3>
    <input type="text" />
    <button on:click={dismiss}>Close</button>
    <button on:click={copy}>Copy</button>
  </section>
<button on:click={importSettings}>Import</button>

<style>
  button {
    bottom: 30px;
    left: 10px;
  }

  section.hidden {
    display: none;
  }

  section {
    position: fixed;
    top: 200px;
    left: calc(50% - 150px - 0.5rem);
    padding: 1rem;
    box-shadow: 6px 6px 9px 4px #222;
    border: 2px solid #222;
    border-radius: 10px;
  }

  :global(main.light section.export) {
    box-shadow: 6px 6px 9px 4px #303030;
    border: 2px solid #303030;
  }

  h3 {
    font-size: 1rem;
    font-family: sans-serif;
    margin: 0 0 12px;
  }

  input {
    width: calc(100% - 0.5rem);
    margin-bottom: 20px;
  }
</style>
