<script>
  import { exampleData } from "./ExampleData.js";
  import CopyInput from "./CopyInput.svelte";
  export let servers = exampleData;
</script>

<style>
  main {
    max-width: 80em;
    margin: 0 auto;
  }
  .server {
    background-color: rgba(0, 0, 0, 0.05);
  }
  .ip {
    float: right;
  }
</style>

<head>
  <meta name="Description" content="A minecraft server list." />
</head>

<main>
  <h1>Minecraft Server List</h1>

  {#each servers as { name, ip, banner }}
    <div class="server">
      <h2>{name}</h2>
      <div class="ip">
        <CopyInput {ip} />
      </div>
      <img src={banner} alt={`${name} banner`} />
    </div>
  {/each}
</main>
