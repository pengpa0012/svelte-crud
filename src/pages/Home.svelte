<script>
  import { Link } from "svelte-routing";
  import Card  from "../lib/Card.svelte"
</script>

<div class="p-5">
  <div class="flex justify-between items-center">
    <h1>Home</h1>
    <ul class="flex gap-5">
      <li>
        <Link to="/profile/12">Profile</Link>
      </li>
      <li>
        <Link to="/login">Logout</Link>
      </li>
    </ul>
  </div>
  <div class="my-12 flex flex-col gap-5">
    {#each [1,2,3] as item}
      <Card />
    {/each}
  </div>
</div>