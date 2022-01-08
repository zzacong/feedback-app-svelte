<script>
  // export let name
  let firstName = 'Zac'
  let lastName = 'Ong'
  let color = 'skyblue'
  let showText = false
  let users = [
    { id: '1', name: 'Tillie Beck' },
    { id: '2', name: 'Harold Bennett' },
    { id: '3', name: 'Rosetta Hale' },
  ]

  $: name = `${firstName} ${lastName}`

  const toggle = () => {
    color = color === 'skyblue' ? 'slateblue' : 'skyblue'
    showText = !showText
    users = [...users, { id: `${users.length + 1}`, name: 'Miguel Ward' }]
  }
</script>

<main>
  <h1 style="color: {color}">Hello {name}!</h1>

  {#if showText}
    <p>
      Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
      how to build Svelte apps.
    </p>
  {:else}
    <p>No text</p>
  {/if}

  <button on:click={toggle}>Click</button>

  {#each users as user (user.id)}
    <h3>{user.id}: {user.name}</h3>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: lightcoral;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
