<script>
  import { exampleData } from "./ExampleData.js";
  export let servers = exampleData;
  export let grabIp = function(text){
    const ips = document.getElementsByClassName('ip');
    const toCopy = Array.from(ips).find(({value}) => value === text);
    toCopy.select();
    document.execCommand("copy");
  }
</script>

<style>
  main {
    max-width: 80em;
    margin: 0 auto;
  }
  .server {
    background-color: rgba(0, 0, 0, 0.05);
  }
  .ipcopy {
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
      <div class="ipcopy">
        <input class="ip" value={ip} readonly><button on:click={() => grabIp(ip)}>Copy</button>
      </div>
      <img src={banner} alt={`${name} banner`} />
    </div>
  {/each}
</main>
