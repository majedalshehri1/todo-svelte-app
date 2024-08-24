<script>
  import { CircleIcon } from "svelte-feather-icons";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let activeEditTodo;
  export let isFilter;

  let value = "";

  const handelAddTodo = () => {
    if (!value.trim()) {
      //trim() is method to check for empty string
      return;
    }
    dispatch("addTodo", value.trim());
    value = ""; // ( value = ""; ) after adding the task will be removed from the queue
  };

  const editChange = () => {
    if (activeEditTodo) {
      value = activeEditTodo.title;
    }
  };
  const handleFilter = () => {
    dispatch("filter");
  };

  $: activeEditTodo, editChange();
</script>

<!-- TodosFrom Structure -->
<div class="todos-form">
  <div class="todos-form_icon" class:active={isFilter} on:click={handleFilter}>
    <CircleIcon />
  </div>
  <div class="todos-form_form">
    <input bind:value type="text" placeholder="أضف مهمة جديدة ..." />
  </div>
  <div class="todos-form_submit" on:click={handelAddTodo}>
    <button class="btn" disabled={!value.trim()}>
      {activeEditTodo ? "تعديل" : "اضافة"}
    </button>
  </div>
</div>
