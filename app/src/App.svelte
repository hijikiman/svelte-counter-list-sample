<script lang="ts">
  import CounterCard from './components/CounterCard.svelte'
  import type { CounterCardValueType } from './types'

  let counterCardList: CounterCardValueType[] = []

  const onClick = () => {
    counterCardList = [...counterCardList, { name: 'hoge', count: 0 }]
  }
</script>

<main>
  <h1>Multiple Counter</h1>
  <button on:click={onClick}>add</button>
  {#each counterCardList as counterCardValue}
    <CounterCard value={counterCardValue} />
  {/each}
  <div class="card" />
</main>

<style>
  h1 {
    font-size: 3.2em;
    line-height: 1.1;
  }
</style>
