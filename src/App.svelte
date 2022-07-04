<script>
  import logo from '@/assets/svelte.png'
  import Counter from '@/lib/Counter.svelte'
  let name = 'Manguito'
  let beltColor = 'black'

  let firstName = 'Pollo'
  let lastName = 'Chicken'

  let people = [
    { name: 'yoshi', beltColour: 'black', age: 25, id: 1 },
    { name: 'mario', beltColour: 'orange', age: 45, id: 2 },
    { name: 'luigi', beltColour: 'brown', age: 35, id: 3 }
  ];

  const svelteUrl = "https://svelte.dev"
  const svelteKitUrl = "https://github.com/sveltejs/kit#readme"

  $: fullName = `${firstName} ${lastName}`
  $: {
    console.log(beltColor)
    console.log(fullName)
  }

  const handleClick = () => {
    beltColor = 'orange'
  }

  const handleInput = (e) => {
    beltColor = e.target.value
  }
</script>

<main>
  <img src={logo} alt="Svelte Logo" />
  <h1>Hello {name}!</h1>
  <button on:click={handleClick} style="color: {beltColor}">{beltColor} belt</button>
  <!-- <input type="text" on:input={handleInput} value={beltColor}> -->
  <p>{fullName}</p>
  <input type="text" bind:value={beltColor}>
  <input type="text" bind:value={firstName}>
  <input type="text" bind:value={lastName}>
  <Counter />

  <p>
    Visit <a href={svelteUrl} >svelte.dev</a> to learn how to build Svelte
    apps.
  </p>

  <p>
    Check out <a href={svelteKitUrl}>SvelteKit</a> for
    the officially supported framework, also powered by Vite!
  </p>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      <p>{person.age} years old, {person.beltColour} belt.</p>
    </div>
  {:else}
    <p>There are no people to show...</p>
  {/each}
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
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
