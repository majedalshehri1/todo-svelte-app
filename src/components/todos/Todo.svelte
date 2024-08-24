<script>
  import { CircleIcon, CheckCircleIcon, EditIcon, Trash2Icon } from "svelte-feather-icons";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let todo;
  export let activeEditTodo;
  const handelEdit = () => {
    dispatch("editTodo", todo);
  };
  const handelDelete = () => {
    dispatch("deleteTodo", todo.id);
  };
  const handelToggelTodo = () => {
    dispatch("toggelTodo", todo.id);
  }
</script>

<div class="todos-todo" class:done={todo.done}>
  <!-- 3 type into the div todo -->
  <div class="todos-todo_icon" on:click={handelToggelTodo}>
    {#if todo.done}
    <CheckCircleIcon/>
      {:else}
      <CircleIcon />
    {/if}
  </div>
  <div class="todos-todo_text">{todo.title}</div>
  {#if !activeEditTodo}
    <div class="todos-todo_cta">
      <div class="todos-todo_cta-edit" on:click={handelEdit}>
        <EditIcon size="20" />
      </div>
      <div class="todos-todo_cta-delete" on:click={handelDelete}>
        <Trash2Icon size="20" />
      </div>
    </div>
  {/if}
</div>
