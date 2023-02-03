<script lang="ts">
  import { writable } from 'svelte/store'
  interface IEvent {
    id: string
    date: string
    time: string
    location: string
    title: string
  }

  const initialState: IEvent = {
    id: '0',
    date: new Date().toDateString(),
    time: '00:00',
    location: '',
    title: ''
  }

  const state = writable<IEvent>(initialState)

  const postNewEvent = () => {
    // console.log('2');
    // state.update(() => {...$state})
    // console.log($state)
  }
</script>

<div class="instructions">
  <h5>{'createNewEntry'}</h5>
  <input type="date" name="date" bind:value={$state.date} />
  <input class="shortInput" type="text" name="time" placeholder="19:30" bind:value={$state.time} />
  <input type="text" name="title" placeholder={'format'} bind:value={$state.title} />
  <input type="text" name="location" placeholder="Dubai Open Club" bind:value={$state.location} />
  <button on:click={postNewEvent}>Create</button>
</div>

<style>
  h5 {
    margin: 0;
    margin-bottom: 12px;
  }
  .shortInput {
    width: 100px;
  }
  .instructions {
    line-height: 1.6;
    margin: 1rem 0;
    border: 1px solid rgba(var(--accent), 25%);
    background-color: white;
    padding: 1rem;
    border-radius: 0.4rem;
  }
  .instructions button {
    margin-top: 12px;
    font-size: 0.875em;
    font-weight: bold;
    background: rgba(var(--accent), 12%);
    color: rgb(var(--accent));
    border: none;
    border-radius: 4px;
    padding: 0.3em 0.45em;
  }
  .instructions strong {
    color: rgb(var(--accent));
  }
</style>
