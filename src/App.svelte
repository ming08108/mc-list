<script>
  import { exampleData } from "./ExampleData.js";
  export let servers = exampleData;
  export let grabDomain = function(text){
    const addresses = document.getElementsByClassName('address');
    const toCopy = Array.from(addresses).find((address) => {return address.value === text});
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
  .addresscopy {
    float: right;
  }
</style>

<head>
  <meta name="Description" content="A minecraft server list." />
</head>

<main>
  <h1>Minecraft Server List</h1>

  {#each servers as { name, address, banner }}
    <div class="server">
      <h2>{name}</h2>
      <div class="addresscopy">
        <input class="address" value={address} readonly><button on:click={() => grabDomain(address)}>Copy</button>
      </div>
      <img src={banner} alt={`${name} banner`} />
    </div>
  {/each}
</main>
