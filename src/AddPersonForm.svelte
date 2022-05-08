<script>
  let name;
  let beltColor;
  let age;
  let skills = [];
  // let fighting = false;
  // let sneaking = false;
  // let running = false;
  const handleSubmit = () => {
    console.log(name, age, fighting, sneaking, running);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="number" placeholder="age" bind:value={age} />
  <label>Skills:</label>
  <!-- <input type="checkbox" bind:checked={fighting} />fighting<br />
  <input type="checkbox" bind:checked={sneaking} />sneaking<br />
  <input type="checkbox" bind:checked={running} />running<br /> -->
  <input type="checkbox" bind:group={skills} value="fighting" />fighting<br />
  <input type="checkbox" bind:group={skills} value="sneaking" />sneaking<br />
  <input type="checkbox" bind:group={skills} value="running" />running<br />
  <label>Belt color:</label>
  <select bind:value={beltColor}>
    <option value="black">black</option>
    <option value="orange">orange</option>
    <option value="brown">brown</option>
    <option value="white">white</option>
  </select>
  <button>Add Ninja</button>
</form>

<style></style>
