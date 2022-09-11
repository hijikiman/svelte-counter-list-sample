<script lang="ts">
  import CounterCard from './components/CounterCard.svelte'
  import type { CounterCardValueType } from './types'

  let new_counter_name = ''
  let counterCardList: CounterCardValueType[] = []
  $: total_count = counterCardList.map((item) => item.count).reduce((sum, item) => sum + item, 0)

  const addCounterCard = () => {
    counterCardList = [...counterCardList, { name: new_counter_name, count: 0 }]
    new_counter_name = ''
  }

  const increment = (id: number) => {
    if (10000 > counterCardList[id].count) {
      counterCardList[id].count += 1
    }
  }
  const decrement = (id: number) => {
    if (counterCardList[id].count > 0) {
      counterCardList[id].count -= 1
    }
  }
  const reset = (id: number) => {
    counterCardList[id].count = 0
  }
  const removeCounterCard = (id: number) => {
    counterCardList.splice(id, 1)
    counterCardList = counterCardList
  }
</script>

<main>
  <h1>Multiple Counter</h1>
  <p>
    total count: {total_count}
  </p>
  <input type="text" bind:value={new_counter_name} />
  <button on:click={addCounterCard}>add</button>
  <ul>
    {#each counterCardList as counterCardValue, id}
      <li>
        <CounterCard
          {...counterCardValue}
          on:inc={() => increment(id)}
          on:dec={() => decrement(id)}
          on:reset={() => reset(id)}
          on:remove={() => removeCounterCard(id)}
        />
      </li>
    {/each}
  </ul>
  <div class="card" />
</main>

<style>
  h1 {
    font-size: 3.2em;
    line-height: 1.1;
  }
  li {
    list-style-type: none;
  }
</style>
