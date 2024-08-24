<!-- Import components to use it -->
<script>
  // Import library navigator to bulid router
  import { Router, Route } from "svelte-navigator";
  import TodoPage from "./pages/TodoPage.svelte";
  import Header from "./components/layout/Header.svelte";
  import AboutPage from "./pages/AboutPage.svelte";
  import Posts from "./pages/Posts.svelte";
</script>

<div class="App">
  <Header />
  <!-- <TodoPage /> -->
  <Router>
    <Route path="/" component={TodoPage} />
    <Route path="/about" component={AboutPage} />
    <Route path="/posts/:id" component={Posts} />
  </Router>
</div>
