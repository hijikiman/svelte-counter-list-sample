<script lang="ts">
  export let count: number = 0

  const increment = () => {
    if (10000 > count) {
      count += 1
    }
  }
  const decrement = () => {
    if (count > 0) {
      count -= 1
    }
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
