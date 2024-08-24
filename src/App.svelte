<!-- Import components to use it -->
<script>
  // Import library navigator to bulid router
  import {} from "svelte-navigator"
  import TodoPage from "./pages/TodoPage.svelte";
  import Header from "./components/layout/Header.svelte";
</script>

<div class="App">
  <Header />
  <TodoPage />
</div>
