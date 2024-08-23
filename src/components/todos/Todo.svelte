<script>
  import { CircleIcon, EditIcon, Trash2Icon } from "svelte-feather-icons";
</script>

<div class="todos-todo">
  <!-- 3 type into the div todo -->
  <div class="todos-todo_icon">
    <CircleIcon />
  </div>
  <div class="todos-todo_text">text</div>
  <div class="todos-todo_cta">
    <div class="todos-todo_cta-edit">
      <EditIcon size="20" />
    </div>
    <div class="todos-todo_cta-delete">
      <Trash2Icon size="20" />
    </div>
  </div>
</div>
