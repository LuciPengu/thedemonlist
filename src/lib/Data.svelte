<script>
  export let val;
  import edemon from "../assets/edemon.png";
  import mdemon from "../assets/mdemon.png";
  import hdemon from "../assets/hdemon.png";
  import idemon from "../assets/idemon.png";
  import exdemon from "../assets/exdemon.png";
  import chroma from 'chroma-js';
  
  const f = chroma.scale(['#824ADB', '#F025FF' , '#FF4848', '#860101', '#000000']);
  
  function getColor(num) {
    return f(num).toString()
  }
</script>

<div class="level">
  <div class="levelTitle">
    {val.level}
    {#if val.rating === "Easy Demon"}
    <img class="difficulty" src="{edemon}"/>
    {:else if val.rating === "Medium Demon"}
    <img class="difficulty" src="{mdemon}"/>
    {:else if val.rating === "Extreme Demon"}
    <img class="difficulty" src="{exdemon}"/>
    {:else if val.rating === "Insane Demon"}
    <img class="difficulty" src="{idemon}"/>
    {:else}
    <img class="difficulty" src="{hdemon}"/>
    {/if}
  </div>
  
  <div class="levelCreator">Creator: {val.creator}</div>
  <div class="levelSong">Song: {val.song}</div>
  <div class="levelRanking">Official Rating: {val.rating}</div>
  <div class="levelRanking">Demon Rank: {val.roundedRanking}</div>
  <div class="levelSpecificRanking">Specific Demon Rank: {val.ranking}</div>
  <div class="levelID">id: {val.id}</div>

  <div class="ratings" style="background-color:{getColor(val.roundedRanking/35)}">
  {#each val.players as player }
      <div class="rating"> 
        {player.player} rated this level {player.ranking}
      </div>
  {/each}
  </div>

</div>
<style>
  
  .difficulty {
    height: 10em;
    width: 10em;
    float: right;
    position: relative;
  }

  .level{
    margin: 1em;
    padding: 1em;
    min-width: 20em;
    text-align: left;
    line-height: 1.75em;
  }

  .ratings{ 
    color: white;
    margin: 2em;
    padding: 2em;
    line-height: 2.5em;
    border-radius: 1em;
  }

  .levelTitle{
    
    font-weight: bold;
    font-size: 1.5em;
    margin-bottom: 0.5em;

  }
</style>