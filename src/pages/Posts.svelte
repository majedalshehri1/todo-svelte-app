<script>
  import { useParams } from "svelte-navigator";
  const params = useParams();
</script>

<h1>Post {$params.id}</h1>
