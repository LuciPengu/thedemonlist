<script>
  import Search from './lib/Search.svelte'
  import Modal from 'svelte-simple-modal';


</script>

<main>
  <h1>THE DEM😈N LIST</h1>
  <Modal><Search/></Modal>

</main>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@700&family=Poppins:ital,wght@0,400;1,300&display=swap');
  
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@700&family=Poppins:wght@700&display=swap');

  
  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
    font-family: 'Poppins', sans-serif;
  }


  :global(body) {
		background-color: white;
		color: black;
		transition: background-color 0.3s
	}


  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }
</style>
