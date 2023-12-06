<script>
  import { Link, navigate } from "svelte-routing";
  function onLogout() {
    localStorage.removeItem("token")
    localStorage.removeItem("username")
    localStorage.removeItem("userId")
    navigate("/login")
  }
</script>

<div class="flex justify-between items-center">
  <Link to="/">Home</Link>
  <ul class="flex gap-5">
    <li>
      <Link to="/profile/12">Profile</Link>
    </li>
    <li>
      <button on:click={onLogout}>Logout</button>
    </li>
  </ul>
</div>