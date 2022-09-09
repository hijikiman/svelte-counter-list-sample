<script lang="ts">
  import CountUpDown from './CountUpDown.svelte'
  import type { CounterCardValueType } from '../types'

  export let value: CounterCardValueType = { name: '', count: 0 }
</script>

<div class="card">
  <span>{value.name}</span>
  <span>{value.count}</span>
  <CountUpDown bind:count={value.count} />
</div>

<style>
</style>
