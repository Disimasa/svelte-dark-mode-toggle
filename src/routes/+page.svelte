<script>
  import DarkModeToggle from '$lib'

  let darkMode = false
</script>

<main class="{darkMode ? 'dark-mode' : 'light-mode'}">
	<DarkModeToggle
  {darkMode}
  size='100'
  on:click={() => darkMode = !darkMode}/>
</main>

<style>
  :global(html, body) {
    width: 100%;
    height: 100%;
    padding: 0;
    margin: 0;
  }

  main {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .light-mode {
    background-color: #FFFFFF;
  }

  .dark-mode {
    background-color: #000000;
  }
</style>