<script>
  import TodosForm from "../components/todos/TodosForm.svelte";
  import Todos from "../components/todos/Todos.svelte";

  let todos = [];

  let activeEditTodo = null;

  let isFilter = false;

  const addTodo = (e) => {
    const title = e.detail;
    const id = new Date().getTime();
    // each ID is to unique number
    // console.log(id);
    if (!activeEditTodo) {
      todos = [
        {
          title,
          // @ts-ignore
          id,
          done: false,
        },
        ...todos,
        // ( ...todos ) that is mean the last version in the list todos
      ];
    } else {
      // Edit Mode
      todos = todos.map((t) => {
        if (activeEditTodo.id === t.id) {
          t.title = title;
        }
        return t;
      });
    }
    activeEditTodo = null;
  };

  const deleteTodo = (e) => {
    const id = e.detail;
    todos = todos.filter((t) => t.id !== id);
  };

  const editTodo = (e) => {
    activeEditTodo = e.detail;
  };
  const toggelTodo = (e) => {
    if (activeEditTodo) {
      return;
    }
    const id = e.detail;
    todos = todos.map((t) => {
      if (t.id === id) {
        t.done = !t.done;
      }
      return t;
    });
  };

  const filter = () => {
    isFilter = !isFilter;
  };

  $: allTodos = isFilter ? todos.filter((t) => !t.done) : todos;
</script>

<main>
  <div class="container">
    <div class="todos">
      <TodosForm
        {activeEditTodo}
        {isFilter}
        on:addTodo={addTodo}
        on:filter={filter}
      />
      <Todos
        todos={allTodos}
        {activeEditTodo}
        on:deleteTodo={deleteTodo}
        on:editTodo={editTodo}
        on:toggelTodo={toggelTodo}
      />
    </div>
  </div>
</main>
