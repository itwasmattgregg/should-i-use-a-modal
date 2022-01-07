<script>
  import { Modals, closeModal, openModal, closeAllModals } from 'svelte-modals';
  import Modal from './Modal.svelte';

  function handleClick() {
    openModal(Modal, {
      title: 'Ok cool...',
      message: `...but what if I need to open another modal on top of this one even though I know it&lsquo;s a bad idea?`,
    });
  }

  function handleKeydown(event) {
    if (event.key === 'Escape') closeAllModals();
  }
</script>

<svelte:window on:keydown={handleKeydown} />

<h1>Should I use a modal?</h1>
<button on:click={handleClick}>Click here to find out</button>

<Modals>
  <div slot="backdrop" class="backdrop" on:click={closeModal} />
</Modals>

<style>
  .backdrop {
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background: rgba(0, 0, 0, 0.5);
  }
</style>
