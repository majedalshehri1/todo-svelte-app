<script>
  import TodosForm from "../components/todos/TodosForm.svelte";
  import Todos from "../components/todos/Todos.svelte";

  let todos = [
    { id: "1", title: "اجتماع لتخطيط مشروع التخرج", done: false },
    { id: "2", title: "تاسكات svelte", done: false },
    { id: "3", title: "اختبار قصير", done: false },
    { id: "4", title: "مذاكرة UX", done: false },
  ];
</script>

<main>
  <div class="container">
    <div class="todos">
      <TodosForm />
      <Todos {todos} />
    </div>
  </div>
</main>
