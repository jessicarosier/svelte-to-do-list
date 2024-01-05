<script>
    import Todos from "./components/Todos.svelte";

   let todos = [
        { id: 1, label: 'Create a Svelte starter app', completed: true },
        { id: 2, label: 'Create your first component', completed: true },
        { id: 3, label: 'Complete the rest of the tutorial', completed: false }
    ];
</script>

<main class="page-wrapper">
  <h1>To Do List</h1>

  <Todos {todos} />

</main>

<style>
    .page-wrapper {
        display: flex;
        flex-direction: column;
        min-height: 100vh;
    }

    .page-wrapper h1 {
        text-align: center;
    }
</style>

