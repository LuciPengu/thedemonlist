<script>

  import { fade } from 'svelte/transition';
  import Level from './Level.svelte'
  
  let searchValue = ""
      let posts = [];

  let promise = Promise.resolve([]);
  
  async function fetchUsers() {
    const response = await self.fetch(`https://gdbackend.hydrabeans.repl.co/getLevel?level=${searchValue}`);

    if (response.ok) {
      return response.json();
      
    } else {
      throw new Error(users);
    }
  }
  	
  function searchLevels() {
    promise = fetchUsers();
  }
  function handleKeydown(event) {
		if(event.keyCode == 13){
      searchLevels();
    }
	}


</script>

<svelte:window on:keydown={handleKeydown}/>

<div class="search">
  <input bind:value={searchValue}>
  <button on:click={searchLevels}>
    Search
  </button>
</div>
{#await promise}
	<p transition:fade>Loading...</p>
{:then levels}
  {#each levels as val }
    <Level val={val}/>
  {/each}
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}

<style>
  input, button{
    font-family: 'Poppins', sans-serif;
    margin: 0.3em;
    padding: 0.75em;
    text-align: left;
    border-radius: 1em;
    border-color: #824ADB;
    border-style: solid;
  }
  input{
    min-width: 20em;
    
  }
  button{
    font-weight: bold;
    min-width: 7em;
    text-align: center;
    background-color: #824ADB;
    color: white;

  }
 .search{
    margin: 2em;
  }
  

</style>
