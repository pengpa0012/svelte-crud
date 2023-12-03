<script>
	import Card from "../lib/Card.svelte";

  let isCreate = true
</script>

<div class="p-5">
  <div class="mb-4 flex flex-col items-center gap-4">
    <img src="https://via.placeholder.com/200x200" alt="profile_image" class="rounded-full">
    <h2>Name</h2>
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
        {#each [1,2,3] as item}
          <Card />
        {/each}
      </div>
    {/if}
  </div>
</div>