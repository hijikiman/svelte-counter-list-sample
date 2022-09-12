<script lang="ts">
  import CountUpDown from './CountUpDown.svelte'
  import CountReset from './CountReset.svelte'
  import CounterName from './CounterName.svelte'
  import CounterRemove from './CounterRemove.svelte'
  import type { CounterCardValueType } from '../types'

  export let name: CounterCardValueType['name'] = ''
  export let count: CounterCardValueType['count'] = 0
</script>

<div class="card">
  <CounterName bind:name />
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
