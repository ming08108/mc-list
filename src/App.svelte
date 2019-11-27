<script>
  import { exampleData } from "./ExampleData.js";
  export let servers = exampleData;
  console.log(exampleData);
  export function grabip(text) {
    let textbox = document.createElement('textarea');
    textbox.value= text['ip'];
    document.body.append(textbox);
    textbox.select();
    document.execCommand("copy");
    textbox.remove();
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
      <h2 class="ip">{ip}<button on:click={() => grabip({ip})}>Copy</button></h2>
      <img src={banner} alt={`${name} banner`} />
    </div>
  {/each}
</main>
