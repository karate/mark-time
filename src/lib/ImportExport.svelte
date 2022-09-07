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
  }
</script>

<button on:click={exportSettings}>Export</button>
  <div class="export hidden">
  <p>Please copy the following string</p>
  <input type="text" />
  <button on:click={dismiss}>Close</button>
  <button on:click={copy}>Copy</button>
</div>
<button on:click={importSettings}>Import</button>
<div class="import hidden"></div>

<style>
  button {
    bottom: 30px;
    left: 10px;
  }

  div.hidden {
    display: none;
  }

  div {
    position: fixed;
    width: 300px;
    height: 300px;
    top: 200px;
    left: calc(50% - 150px - 0.5rem);
    background-color: #095895;
    padding: 1rem;
    box-shadow: 0 0 12px 12px #222;
    border-radius: 10px;
  }

textarea {
  width: 100%;

}
</style>
