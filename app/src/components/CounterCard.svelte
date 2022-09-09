<script lang="ts">
  import type { CounterCardValueType } from '../types'

  export let value: CounterCardValueType = { name: '', count: 0 }
</script>

<div class="card">
  <span>{value.name}</span>
  <span>{value.count}</span>
</div>

<style>
</style>
