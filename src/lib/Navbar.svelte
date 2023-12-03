<script>
  import { Link } from "svelte-routing";
</script>

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