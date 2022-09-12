<script lang="ts">
  import { createEventDispatcher } from 'svelte'

  export let name: string = ''
  export let MAX_NAME_LENGTH: number = 5
  let new_name: string = name
  let err: boolean = false
  const dispatch = createEventDispatcher()

  const onUpdate = () => {
    err = false
    if (new_name.length == 0 || new_name.length > MAX_NAME_LENGTH) {
      setTimeout(() => {
        err = true
      }, 100)
      new_name = name
      return
    }
    dispatch('change', { value: new_name })
  }
</script>

<form on:submit|preventDefault={onUpdate}>
  <input class={err && 'err'} type="text" bind:value={new_name} on:blur={onUpdate} />
</form>

<style>
  form {
    display: inline-block;
  }

  .err {
    animation: 2s notice;
  }

  @keyframes notice {
    0% {
      background-color: #552233;
    }
    100% {
      background-color: #3a3a3a;
    }
  }
</style>
