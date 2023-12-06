<script lang="ts">
  import axios from "axios"
	import { onMount } from "svelte";
  import { allPosts } from "../store"
  import Auth from "../lib/Auth.svelte";
  import Card  from "../lib/Card.svelte"
  let allPostVal: any = []

  onMount(() => {
    axios.get(`${import.meta.env.VITE_ENDPOINT}/post/getAllPosts`, {
      headers: {
        "x-access-token": localStorage.getItem("token")
      }
    }).then(res => {
      $allPosts = res.data.Posts
      allPosts.subscribe((value) => { 
        allPostVal = value
      }); 
    })
  })
</script>

<Auth />

<div class="p-5">
  <h2 class="mt-12 text-2xl">Blog Posts</h2>
  <div class="my-6 flex flex-col gap-5">
    {#each allPostVal as item}
      <Card user={item} />
    {/each}
  </div>
</div>