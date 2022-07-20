<script>
  export let val;
  
  import { fade } from 'svelte/transition';
  import edemon from "../assets/edemon.png";
  import mdemon from "../assets/mdemon.png";
  import hdemon from "../assets/hdemon.png";
  import idemon from "../assets/idemon.png";
  import exdemon from "../assets/exdemon.png";
  import { getContext } from 'svelte';
  import Data from './Data.svelte';
  const { open } = getContext('simple-modal');
  const showSurprise = (val) => open(Data, { val: val });
  import chroma from 'chroma-js';
  
  const f = chroma.scale(['#824ADB', '#F025FF' , '#FF4848', '#860101', '#000000']);
  function getColor(num) {
    return f(num).toString()
  }

</script>

  <button transition:fade class="level" on:click={showSurprise(val)} style="background-color:{getColor(val.roundedRanking/35)}">
    
    <div class="levelTitle">
      {val.level}
      {#if val.rating === "Easy Demon"}
      <img transition:fade class="difficulty" src="{edemon}"/>
      {:else if val.rating === "Medium Demon"}
      <img transition:fade class="difficulty" src="{mdemon}"/>
      {:else if val.rating === "Extreme Demon"}
      <img transition:fade class="difficulty" src="{exdemon}"/>
      {:else if val.rating === "Insane Demon"}
      <img transition:fade class="difficulty" src="{idemon}"/>
      {:else}
      <img transition:fade class="difficulty" src="{hdemon}"/>
      {/if}
    </div>
    
    <div class="levelCreator">by {val.creator}</div>
    <div class="levelRanking">demon rank {val.roundedRanking}</div>
    
  </button>

<style>
  .difficulty {
    height: 4.4em;
    width: 4.4em;
    float: right;
    position: relative;
    
  }

  .levelTitle{
    font-weight: bold;
  }

  .level{
    font-family: 'Poppins', sans-serif;
    color: white;
    margin: 1em;
    padding: 1em;
    min-width: 20em;
    text-align: left;
    border-radius: 1em;
    border: none;
  }
</style>