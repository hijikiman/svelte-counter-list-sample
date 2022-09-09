<script lang="ts">
  export let count: number = 0

  const increment = () => {
    count += 1
  }
  const decrement = () => {
    count -= 1
  }
</script>

<div class="button-group">
  <button on:click={increment}>+</button>
  <button on:click={decrement}>-</button>
</div>

<style>
  .button-group {
    display: inline-block;
  }
</style>
