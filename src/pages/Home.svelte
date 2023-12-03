<script>
  import Card  from "../lib/Card.svelte"
</script>

<div class="p-5">
  <div class="my-12 flex flex-col gap-5">
    {#each [1,2,3] as item}
      <Card />
    {/each}
  </div>
</div>