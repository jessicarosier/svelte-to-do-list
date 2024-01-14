<script>

    import { slide } from 'svelte/transition';

  let toDoItems = [
      {
          name: "Study for exam.",
          completed: true,
      },
      {
          name: "Feed the dog.",
          completed: false,
      },
      {
          name: "Clean the cats litter box.",
          completed: false,
      },
  ];

  let name = "";

  function addToDo() {
      const newItem = {
          name: name,
          completed: false,
      }

      toDoItems = [...toDoItems, newItem]
      name = "";
  }

</script>


<div>
  <input type="text" bind:value={name} />
  <button on:click={addToDo} >Add Todo</button>
</div>

<div>
  <ul>
    {#each toDoItems.filter(todo => todo.completed) as todo}
      <li transition:slide>
        {todo.name}
        <input type="checkbox" bind:checked={todo.completed} />
      </li>
      {/each}
  </ul>

  <ul>
    {#each toDoItems.filter(todo => !todo.completed) as todo}
      <li transition:slide>
        {todo.name}
        <input type="checkbox" bind:checked={todo.completed} />
      </li>
    {/each}
  </ul>
</div>


<style>

  div {
      display: flex;
      justify-content: center;
      align-items: center;
  }

</style>