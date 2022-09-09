<script lang="ts">
  import CountUpDown from './CountUpDown.svelte'
  import CountReset from './CountReset.svelte'
  import type { CounterCardValueType } from '../types'

  export let value: CounterCardValueType = { name: '', count: 0 }
</script>

<div class="card">
  <span>{value.name}</span>
  <span>{value.count}</span>
  <div class="count-controller">
    <CountUpDown bind:count={value.count} />
    <CountReset bind:count={value.count} />
  </div>
</div>

<style>
  .count-controller {
    display: inline-block;
  }
</style>
