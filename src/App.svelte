<script>
  //Svelte requires id for loops
  let people = [
    { name: "yoshi", beltColour: "black", age: 25, id: 1 },
    { name: "mario", beltColour: "orange", age: 45, id: 2 },
    { name: "luigi", beltColour: "brown", age: 35, id: 3 },
  ];

  const handleClick = (e, id) => {
    //delete the person from people, if id not equal to selected, keep id, else, filter out
    //need to reassign people
    people = people.filter((el) => el.id !== id);
    console.log(e);
  };
</script>

<main>
  <!-- Svelte loop template -->
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      <p>{person.age} years old, {person.beltColor} belt.</p>
      <!-- here we use backpack to return a function without invoking it -->
      <button
        on:click={(e) => {
          handleClick(e, person.id);
        }}>delete</button
      >
    </div>
    <!-- if there is no element in people -->
  {:else}
    <p>There are no people to show</p>
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
