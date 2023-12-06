<script lang="ts">
  import axios from "axios"
	import { onMount } from "svelte";
	import Auth from "../lib/Auth.svelte";
  let post: any = {}
  onMount(() => {
    axios.get(`${import.meta.env.VITE_ENDPOINT}/post/getAllPosts`, {
      headers: {
        "x-access-token": localStorage.getItem("token")
      }
    }).then(res => {
      post = res.data.Posts.find((el:any) => el._id == location.pathname.split("/post/").at(-1))
    })
  })
</script>

<Auth />
<div class="p-5">
  <img src="https://via.placeholder.com/1200x500" alt="banner">
  <div class="flex justify-between items-center my-4">
    <h1>{post.username}</h1>
    <p>{post.date}</p>
  </div>
  <p>{post.description}</p>
</div>