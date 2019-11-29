<script>
  import Icon from "fa-svelte";
  import { faCopy } from "@fortawesome/free-solid-svg-icons/faCopy";
  export let ip;

  const copyIcon = faCopy;
  let inputfield;
  const grabIp = function() {
    inputfield.select();
    document.execCommand("copy");
  };
</script>

<style>
  button {
    border: none;
    background-color: #008cba;
    color: white;
    padding: 0.5em;
  }
  input {
    border: none;
    width: 25em;
  }
  div {
    display: flex;
  }
</style>

<div>
  <input bind:this={inputfield} value={ip} readonly />
  <button on:click={grabIp}>
    <Icon icon={copyIcon} />
    Copy
  </button>
</div>
