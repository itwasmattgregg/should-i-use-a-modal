<script>
  import { Focus } from 'focus-svelte';

  export let modal;
  export let onClose;
  export let onOpen;

  const { title, body, cancel, accept } = modal;
</script>

<Focus enabled>
  <div role="dialog" class="modal">
    <div class="contents rounded-lg shadow-xl">
      <h2 class="text-2xl mb-4">{@html title}</h2>
      <p>{@html body}</p>
      <div class="actions">
        <button
          class="p-4 py-2 rounded-lg border border-yellow-700 text-yellow-700 
				font-bold shadow-lg "
          on:click={onClose}>{@html cancel}</button
        >
        <button
          class="p-4 py-3 rounded-lg bg-yellow-700 text-white 
				font-bold border-none shadow-lg hover:bg-yellow-800 focus:bg-yellow-800"
          on:click={onOpen}>{@html accept}</button
        >
      </div>
    </div>
  </div>
</Focus>

<div class="backdrop" on:click={onClose} />

<style>
  .backdrop {
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background: rgba(0, 0, 0, 0.1);
  }
  .modal {
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 2;

    /* allow click-through to backdrop */
    pointer-events: none;
  }

  .contents {
    width: 400px;
    padding: 24px;
    background: white;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    pointer-events: auto;
    max-width: 100%;
  }

  .actions {
    margin-top: 32px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>
