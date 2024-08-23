<script>
  import { CircleIcon, EditIcon, Trash2Icon } from "svelte-feather-icons";
  export let todo;
</script>

<div class="todos-todo" class:done= {todo.done}>
  <!-- 3 type into the div todo -->
  <div class="todos-todo_icon">
    <CircleIcon />
  </div>
  <div class="todos-todo_text">{todo.title}</div>
  <div class="todos-todo_cta">
    <div class="todos-todo_cta-edit">
      <EditIcon size="20" />
    </div>
    <div class="todos-todo_cta-delete">
      <Trash2Icon size="20" />
    </div>
  </div>
</div>
