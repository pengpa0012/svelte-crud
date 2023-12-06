<script lang="ts">
  import axios from "axios"
	import { onMount } from "svelte";
	import Auth from "../lib/Auth.svelte";
	import Card from "../lib/Card.svelte";
  let profile: any = {}
  let allPosts: any = []
  let isCreate = true
  onMount(() => {
    Promise.all([
      axios.get(`${import.meta.env.VITE_ENDPOINT}/user/getUser?username=${localStorage.getItem("username")}`, {
        headers: {
          "x-access-token": localStorage.getItem("token")
        }
      }),
      axios.get(`${import.meta.env.VITE_ENDPOINT}/post/getAllPosts`, {
        headers: {
          "x-access-token": localStorage.getItem("token")
        }
      })
    ]).then(([user, posts]) => {
      profile = user.data.user
      allPosts = posts.data.Posts.filter((el: any) => el.username == localStorage.getItem("username"))
    })
  })
</script>

<Auth />
<div class="p-5">
  <div class="mb-4 flex flex-col items-center gap-4">
    <img src="https://via.placeholder.com/200x200" alt="profile_image" class="rounded-full">
    <h2>{profile.username}</h2>
  </div>
  <div class="flex gap-5">
    <button on:click={() => isCreate = true}>Create Post</button>
    <button on:click={() => isCreate = false}>Posts</button>
  </div>
  <div class="my-4">
    {#if isCreate}
      <form class="flex flex-col gap-5" on:submit|preventDefault={(e) => console.log(e)}>
        <input type="file" name="image" />
        <input type="text" placeholder="Title" class="border rounded-md p-2" name="title">
        <textarea class="min-h-[200px] max-h-[500px] border rounded-md p-2" placeholder="Description" name="description"></textarea>
        <button type="submit" class="bg-green-500 hover:bg-green-600 text-white rounded-md py-2">Post</button>
      </form>
    {:else}
      <div class="my-6 flex flex-col gap-5">
        {#if allPosts.length > 0}
          {#each allPosts as item}
            <Card user={item} />
          {/each}
        {:else}
          <p class="text-center text-2xl my-12">No Posts</p>
        {/if}
      </div>
    {/if}
  </div>
</div>