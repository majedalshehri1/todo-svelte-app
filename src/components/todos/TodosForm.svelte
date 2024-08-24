<script>
  import { CircleIcon } from "svelte-feather-icons";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  let value = "";
  const handelAddTodo = () => {
    if (!value.trim()) {
      //trim() is method to check for empty string
      return;
    }
    dispatch("addTodo", value.trim());
  };
</script>

<!-- TodosFrom Structure -->
<div class="todos-form">
  <div class="todos-form_icon">
    <CircleIcon />
  </div>
  <div class="todos-form_form">
    <input bind:value type="text" placeholder="أضف مهمة جديدة ..." />
  </div>
  <div class="todos-form_submit" on:click={handelAddTodo}>
    <button class="btn" disabled={!value.trim()}> اضافة </button>
  </div>
</div>
