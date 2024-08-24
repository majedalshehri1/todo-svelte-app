<script>
  import TodosForm from "../components/todos/TodosForm.svelte";
  import Todos from "../components/todos/Todos.svelte";

  let todos = [
    { id: "1", title: "اجتماع لتخطيط مشروع التخرج", done: false },
    { id: "2", title: "تاسكات svelte", done: true },
    { id: "3", title: "اختبار قصير", done: false },
    { id: "4", title: "مذاكرة UX", done: true },
  ];

  let activeEditTodo = null;

  const addTodo = (e) => {
    const title = e.detail;
    const id = new Date().getTime();
    // each ID is to unique number
    // console.log(id);
    if (!activeEditTodo) {
      todos = [
        {
          title,
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
        return t
      });
    }
    activeEditTodo = null
  };

  const deleteTodo = (e) => {
    const id = e.detail;
    todos = todos.filter((t) => t.id !== id);
  };

  const editTodo = (e) => {
    activeEditTodo = e.detail;
  };
</script>

<main>
  <div class="container">
    <div class="todos">
      <TodosForm {activeEditTodo} on:addTodo={addTodo} />
      <Todos
        {todos}
        {activeEditTodo}
        on:deleteTodo={deleteTodo}
        on:editTodo={editTodo}
      />
    </div>
  </div>
</main>
