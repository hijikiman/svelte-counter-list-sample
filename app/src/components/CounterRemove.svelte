<script lang="ts">
  import { createEventDispatcher } from 'svelte'

  const dispatch = createEventDispatcher()
  const onClick = () => dispatch('remove')
</script>

<button on:click={onClick}>×</button>

<style>
</style>
