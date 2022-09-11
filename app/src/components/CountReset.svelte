<script lang="ts">
  import { createEventDispatcher } from 'svelte'

  const dispatch = createEventDispatcher()
  const onClick = () => dispatch('reset')
</script>

<div>
  <button on:click={onClick}>0</button>
</div>

<style>
  div {
    display: inline-block;
  }
</style>
