<script>
  import { Link } from "svelte-routing"
  export let user = {
    _id: "",
    username: "",
    date: "",
    description: ""
  }
</script>

<Link to={`/post/${user._id}`}>
  <div class="border rounded-md p-5 cursor-pointer">
    <div class="flex justify-between items-center">
      <h2 class="text-2xl mb-4">{user.username}</h2>
      <p>{user.date}</p>
    </div>
    <p>{user.description}</p>
  </div>
</Link>