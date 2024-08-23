<script>
  import Todo from "./Todo.svelte";
  // To use prompt in the component use export
  export let todos = [];
</script>

<div class="todos-list">
  <!-- Loops in Svelte use: {#each  as } {/each} -->
  {#each todos as todo (todo.id)}
    <Todo {todo} on:deleteTodo/>
  {/each}
</div>
