<script>
  let inputfield;
  export let ip;

  let grabIp = function() {
    inputfield.select();
    document.execCommand("copy");
  };
</script>

<input bind:this={inputfield} value={ip} readonly />
<button on:click={grabIp}>Copy</button>
