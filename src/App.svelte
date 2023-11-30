<script>
  import { Router, Link, Route } from "svelte-routing";
  import Login from "./pages/Login.svelte";
  import Profile from "./pages/Profile.svelte";
  export let url = "";

</script>

<main>
  <Router {url}>
    <nav>
      <Link to="/">Home</Link>
      <Link to="/profile/testuser">Profile</Link>
    </nav>
    <div>
      <Route path="/profile/:id" component={Profile} />
      <Route path="/login" component={Login} />
      <Route path="/"> <h1 class="text-5xl text-center my-20">Home</h1></Route>
    </div>
  </Router>
 
</main>

