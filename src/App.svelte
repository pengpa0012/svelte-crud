<script>
  import { Router, Link, Route } from "svelte-routing";
  import Login from "./pages/Login.svelte";
  import Profile from "./pages/Profile.svelte";
  import Home from "./pages/Home.svelte";
  export let url = "";

</script>

<main>
  <Router {url}>
    <div>
      <Route path="/profile/:id" component={Profile} />
      <Route path="/login" component={Login} />
      <Route path="/" component={Home} />
    </div>
  </Router>
</main>

