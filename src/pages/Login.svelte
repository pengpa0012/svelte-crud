<script lang="ts">
  let isLogin = true
  let values = {
    username: "",
    repeat_password: "",
    password: ""
  }
  function onSubmit() {
    console.log(values)
  }

</script>

<div class="grid place-items-center min-h-screen">
  <div>
    <h1 class="text-2xl text-center mb-5">Svelte CRUD</h1> 
    <form class="flex flex-col gap-5" on:submit|preventDefault={onSubmit}>
      <input type="text" placeholder="Username" bind:value={values.username} class="p-2 border p-2 focus:outline-none rounded-md">
      <input type="password" placeholder="Password" bind:value={values.password} class="p-2 border p-2 focus:outline-none rounded-md">
      {#if !isLogin}
        <input type="password" placeholder="Repeat Password" bind:value={values.repeat_password} class="p-2 border p-2 focus:outline-none rounded-md">
      {/if}
      <button type="submit" class="bg-green-500 hover:bg-green-600 py-2 rounded-md text-white">Login</button>
      {#if !isLogin}
        <p class="mt-2">Already have an account? login <button class="text-blue-500 underline" on:click={() => isLogin = true}>here</button></p>
      {:else}
        <p class="mt-2">No account yet? signup <button class="text-blue-500 underline" on:click={() => isLogin = false}>here</button></p>
      {/if}
    </form>
  </div>
</div>