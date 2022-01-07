<script>
  import { Modals, closeModal, openModal } from 'svelte-modals';
  import Modal from './Modal.svelte';

  function handleClick() {
    openModal(Modal, { title: 'Alert', message: 'This is an alert' });
  }
</script>

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
