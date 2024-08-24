<script>
  import TodosForm from "../components/todos/TodosForm.svelte";
  import Todos from "../components/todos/Todos.svelte";

  let todos = [
    { id: "1", title: "اجتماع لتخطيط مشروع التخرج", done: false },
    { id: "2", title: "تاسكات svelte", done: true },
    { id: "3", title: "اختبار قصير", done: false },
    { id: "4", title: "مذاكرة UX", done: true },
  ];

  const addTodo = (e) => {
    const title = e.detail;
    const id = new Date().getTime();
    // each ID is to unique number
    // console.log(id);

    // ( ...todos ) that is mean the last version in the list todos
    todos = [
      {
        title,
        id,
        done: false,
      },
      ...todos,
    ];
    todos.push();
  };

  const deleteTodo = (e) => {
    const id = e.detail;
    todos = todos.filter((t) => t.id !== id);
  };
</script>

<main>
  <div class="container">
    <div class="todos">
      <TodosForm on:addTodo={addTodo} />
      <Todos {todos} on:deleteTodo={deleteTodo} />
    </div>
  </div>
</main>
