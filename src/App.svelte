<script>
  import AddPeople from "./AddPeople.svelte";
  import Modal from "./Modal.svelte";

  let showModal = false;

  let people = [
    { name: "yoshi", beltColour: "black", age: 25, id: 1 },
    { name: "mario", beltColour: "orange", age: 45, id: 2 },
    { name: "luigi", beltColour: "brown", age: 35, id: 3 },
  ];

  const handleClick = (id) => {
    people = people.filter((person) => person.id != id);
  };

  const toggle = () => {
    showModal = !showModal;
  };

  const addPerson = (e) => {
    people = [...people, e.detail];
    showModal = false;
  };
</script>

<main>
  <Modal message="sign up" {showModal} on:click={toggle}>
    <AddPeople on:addPerson={addPerson} />
  </Modal>
  <button on:click={toggle}>Show modal</button>
  {#each people as person (person.id)}
    <div>
      <p>{person.name}</p>
      {#if person.beltColour === "black"}
        <p>Master</p>
      {/if}
      <p>{person.beltColour}</p>
      <p>{person.age}</p>
      <button on:click={() => handleClick(person.id)}>Delete</button>
    </div>
  {:else}
    <p>Array is empty</p>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  /* .test{
	color: {belt};
  } */

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
