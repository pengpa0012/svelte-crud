<script lang="ts">
  import Auth from "../lib/Auth.svelte";
  import Card  from "../lib/Card.svelte"
</script>

<Auth />

<div class="p-5">
  <h2 class="mt-12 text-2xl">Blog Posts</h2>
  <div class="my-6 flex flex-col gap-5">
    {#each [1,2,3] as item}
      <Card />
    {/each}
  </div>
</div>