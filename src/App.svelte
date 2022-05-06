<script>
  let firstName = "Jimi";
  let lastName = "Hendrix";
  let beltColor = "black";
  //  Reactive values, like Vue's computed properties
  $: fullName = `${firstName} ${lastName}`;
  // Reactive statement, similar to reactive values
  // $: console.log(beltColor);
  // if any of the following values change, the code block re-runs
  $: {
    console.log(beltColor);
    console.log(fullName);
  }

  const handleClick = () => {
    beltColor = "orange";
  };

  const handleInput = (e) => {
    beltColor = e.target.value;
  };
</script>

<main>
  <!-- Reactive values, like Vue's computed properties -->
  <p>{fullName} {beltColor} belt</p>
  <input type="text" bind:value={firstName} />
  <input type="text" bind:value={lastName} />
  <input type="text" bind:value={beltColor} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
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
