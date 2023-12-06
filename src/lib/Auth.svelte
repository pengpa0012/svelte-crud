<script lang="ts">
	import { onDestroy, onMount } from "svelte";
	import { navigate } from "svelte-routing";
  import {isLoggedIn} from "../store"

  let isLoggedInVal: Boolean
  const unsubscribe = isLoggedIn.subscribe((value) => isLoggedInVal = value)
  onMount(() => {
    const userId = localStorage.getItem("userId")
    if(!userId) navigate("/login")
  })
  onDestroy(unsubscribe)

</script>