<script>
  //import Modal
  import Modal from "./Modal.svelte";
  let showModal = false;
  const toggleModal = () => {
    showModal = !showModal;
  };
  let people = [
    { name: "yoshi", beltColor: "black", age: 25, id: 1 },
    { name: "mario", beltColor: "orange", age: 45, id: 2 },
    { name: "luigi", beltColor: "brown", age: 35, id: 3 },
  ];

  const handleClick = (e, id) => {
    people = people.filter((el) => el.id != id);
    console.log(e);
  };

  let num = 5;
</script>

<!-- output Modal -->
<!-- <Modal message="Hey I am a prop value" showModal ={showModal} /> -->
<!-- when prop name and prop value name the same, use the following shorthand, similar to constructor this.x = x -->
<!-- an event is forwarded back onto Modal component -->
<Modal message="Hey there again" {showModal} on:click={toggleModal} />
<main>
  <button on:click={toggleModal}>Open Modal</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColor === "black"}
        <p><strong>MASTER NINJA</strong></p>
      {/if}
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
