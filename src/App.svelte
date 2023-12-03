<script>
  import { Router, Route } from "svelte-routing";
  import Login from "./pages/Login.svelte";
  import Profile from "./pages/Profile.svelte";
  import Post from "./pages/Post.svelte";
  import Home from "./pages/Home.svelte";
	import Navbar from "./lib/Navbar.svelte";
  export let url = "";
</script>

<main>
  <Router {url}>
    <div class="max-w-[1200px] mx-auto">
      <Route path="/profile/:id">
        <div class="p-5">
          <Navbar />
        </div>
        <Profile />
      </Route>
      <Route path="/post/:id">
        <div class="p-5">
          <Navbar />
        </div>
        <Post />
      </Route>
      <Route path="/login" component={Login} />
      <Route path="/">
        <div class="p-5">
          <Navbar />
        </div>
        <Home />
      </Route>
    </div>
  </Router>
</main>

