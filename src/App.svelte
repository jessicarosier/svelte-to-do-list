<script>
import Todos from "./components/Todos.svelte";

</script>

<main class="page-wrapper">

  <h1>To Do List</h1>

  <Todos />

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

