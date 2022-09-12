<script lang="ts">
  import CountUpDown from './CountUpDown.svelte'
  import CountReset from './CountReset.svelte'
  import CounterName from './CounterName.svelte'
  import CounterRemove from './CounterRemove.svelte'
  import type { CounterCardValueType } from '../types'

  export let name: CounterCardValueType['name'] = ''
  export let count: CounterCardValueType['count'] = 0
  export let MAX_NAME_LENGTH: number = 5
</script>

<div class="card">
  <CounterName {MAX_NAME_LENGTH} bind:name on:change />
  <span class="count">{count}</span>
  <div class="count-controller">
    <CountUpDown on:inc on:dec />
    <CountReset on:reset />
  </div>
  <CounterRemove on:remove />
</div>

<style>
  .count-controller {
    display: inline-block;
  }
  .count {
    display: inline-block;
    min-width: 3em;
  }
</style>
