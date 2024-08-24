<script>
  import Todo from "./Todo.svelte";
  // To use prompt in the component use export
  export let todos = [];
  export let activeEditTodo;
  // ( $: ) to check if the current todo is active and if not active.
  $: activeTodos = activeEditTodo ? [activeEditTodo] : todos; // if in the activeEditTodo, Return just [activeEditTodo] with array ( : or ) return All todos
</script>

<div class="todos-list">
  <!-- Loops in Svelte use: {#each  as } {/each} -->
  {#each activeTodos as todo (todo.id)}
    <Todo {todo} {activeEditTodo} on:deleteTodo on:editTodo on:toggelTodo />
  {/each}

  {#if todos.length === 0}
    <h3 class="no-todos">لايوجد مهام حالياً ...</h3>
  {/if}
</div>
