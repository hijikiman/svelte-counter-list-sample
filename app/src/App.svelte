<script lang="ts">
  import CounterCard from './components/CounterCard.svelte'
  import type { CounterCardValueType } from './types'

  const MAX_NAME_LENGTH = 10
  let new_counter_name = ''
  let validateError = ''
  let counterCardList: CounterCardValueType[] = []
  $: total_count = counterCardList.map((item) => item.count).reduce((sum, item) => sum + item, 0)

  const validateName = (new_name: string) => {
    if (new_name.length == 0) {
      validateError = 'Counter name is required.'
      return false
    }
    if (new_name.length > MAX_NAME_LENGTH) {
      validateError = `Counter name is limited to ${MAX_NAME_LENGTH} characters.`
      return false
    }
    validateError = ''
    return true
  }

  const changeCounterName = (event: { detail: { value: string } }, id: number) => {
    if (!validateName(event.detail.value)) return
    counterCardList[id].name = event.detail.value
  }
  const addCounterCard = () => {
    if (!validateName(new_counter_name)) return
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
  <form on:submit|preventDefault={addCounterCard}>
    <input type="text" bind:value={new_counter_name} />
    <span style="color:{new_counter_name.length > MAX_NAME_LENGTH ? 'red' : 'inherit'}"
      >{new_counter_name.length}/{MAX_NAME_LENGTH}</span
    >
    <button type="submit">add</button>
  </form>
  {#if validateError.length != 0}
    <p class="validate-error">{validateError}</p>
  {/if}
  <ul>
    {#each counterCardList as counterCardValue, id}
      <li>
        <CounterCard
          {...counterCardValue}
          {MAX_NAME_LENGTH}
          on:change={(e) => changeCounterName(e, id)}
          on:inc={() => increment(id)}
          on:dec={() => decrement(id)}
          on:reset={() => reset(id)}
          on:remove={() => removeCounterCard(id)}
        />
      </li>
    {:else}
      <p class="no-counter">There is no counter.</p>
    {/each}
  </ul>
</main>

<style>
  h1 {
    font-size: 3.2em;
    line-height: 1.1;
  }
  li {
    list-style-type: none;
  }
  .validate-error {
    font-size: 0.7em;
    color: red;
  }
  ul {
    margin-top: 2em;
  }
  li:not(:first-child) {
    margin-top: 0.7em;
  }
  .no-counter {
    background-color: #2c2c2c;
    color: darkgray;
    width: 420px;
    padding: 0.5em 2em;
    border-radius: 1em;
  }
</style>
