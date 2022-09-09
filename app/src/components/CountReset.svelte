<script lang="ts">
  export let count: number = 0
</script>

<div>
  <button on:click={() => (count = 0)}>0</button>
</div>

<style>
  div {
    display: inline-block;
  }
</style>
