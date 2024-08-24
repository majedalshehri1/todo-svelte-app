<script>
  import { useParams } from "svelte-navigator";
  const params = useParams();
</script>

<h1 style="text-align: center;">Post {$params.id}</h1>
<p>{$params}</p>
