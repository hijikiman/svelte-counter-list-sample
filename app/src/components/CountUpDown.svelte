<script lang="ts">
  import { createEventDispatcher } from 'svelte'

  const dispatch = createEventDispatcher()
  const onClickPlus = () => dispatch('inc')
  const onClickMinus = () => dispatch('dec')
</script>

<div class="button-group">
  <button on:click={onClickPlus}>+</button>
  <button on:click={onClickMinus}>-</button>
</div>

<style>
  .button-group {
    display: inline-block;
  }
</style>
