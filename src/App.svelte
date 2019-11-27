<script>
  import { exampleData } from "./ExampleData.js";
  export let servers = exampleData;
  export let grabDomain = function(text){
    const domains = document.getElementsByClassName('domain');
    const toCopy = Array.from(domains).filter((domain) => {return domain.value === text})[0];
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
  .domaincopy {
    float: right;
  }
</style>

<head>
  <meta name="Description" content="A minecraft server list." />
</head>

<main>
  <h1>Minecraft Server List</h1>

  {#each servers as { name, domain, banner }}
    <div class="server">
      <h2>{name}</h2>
      <div class="domaincopy">
        <input class="domain" value={domain} readonly><button on:click={() => grabDomain(domain)}>Copy</button>
      </div>
      <img src={banner} alt={`${name} banner`} />
    </div>
  {/each}
</main>
