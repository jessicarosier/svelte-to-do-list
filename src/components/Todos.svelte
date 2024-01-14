<script>

    import {slide} from "svelte/transition";

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
        };

        toDoItems = [...toDoItems, newItem];
        name = "";
    }

    //when the delete button is clicked  it will remove the item from the array
    function deleteToDo() {
        toDoItems = toDoItems.filter(todo => !todo.completed);
    }


</script>


<div>
  <input type="text" bind:value={name}/>
  <button on:click={addToDo}>Add Todo</button>

</div>


<div>

  <h2>{toDoItems.filter(todo => !todo.completed).length} items of {toDoItems.length} left to do.</h2>


  <ul>
    {#each toDoItems.filter(todo => !todo.completed) as todo}
      <li transition:slide>
        <input type="checkbox" bind:checked={todo.completed}/>
        {todo.name}
        <button>Delete</button>
      </li>
    {/each}
  </ul>

  <ul>
    {#each toDoItems.filter(todo => todo.completed) as todo}
      <li transition:slide>
        <input type="checkbox" bind:checked={todo.completed}/>
        {todo.name}
        <button on:click={deleteToDo}>Delete</button>
      </li>
    {/each}
  </ul>
</div>


<style>

    div {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    h2 {
        text-align: center;
    }

    ul {
        list-style: none;
    }

</style>