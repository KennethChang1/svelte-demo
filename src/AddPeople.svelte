<script>
  import { createEventDispatcher } from "svelte";

  let dispatch = createEventDispatcher();

  let name;
  let belt;
  let age;

  const handleSubmit = () => {
    const person = {
      name,
      beltColour: belt,
      age,
      id: Math.random(),
    };

    dispatch("addPerson", person);

    name = "";
    age = "";
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="number" placeholder="age" bind:value={age} />
  <label for="belt">Belt</label>
  <select bind:value={belt}>
    <option value="black">Black</option>
    <option value="orange">Orange</option>
    <option value="brown">Brown</option>
    <option value="white">White</option>
  </select>
  <button>Add person</button>
</form>

<style></style>
