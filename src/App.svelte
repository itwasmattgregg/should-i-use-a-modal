<script>
  import Modal from './Modal.svelte';
  import modalData from './modals';

  let modals = [];

  function handleClick() {
    modals = [
      ...modals,
      {
        title: 'Ok cool...',
        body: '...but what if I need to open another modal on top of this one even though I know it&lsquo;s a bad idea?',
        cancel: 'Nah',
        accept: 'Definitely',
      },
    ];
  }

  function handleKeydown(event) {
    if (event.key === 'Escape') closeAllModals();
  }

  function openNewModal() {
    const randomModal = modalData[Math.floor(Math.random() * modalData.length)];
    modals = [...modals, randomModal];
  }

  function closeModal() {
    modals.pop();
    modals = modals;
  }

  function closeAllModals() {
    modals = [];
  }
</script>

<svelte:window on:keydown={handleKeydown} />

<div class="flex justify-center items-center h-screen">
  <div class="text-center">
    <h1 class="text-4xl mb-8">Should I use a modal?</h1>
    <button
      class="p-4 rounded-lg bg-yellow-700 text-white 
				font-bold border-none shadow-lg hover:bg-yellow-800 focus:bg-yellow-800"
      on:click={handleClick}>Click here to find out</button
    >
  </div>
</div>
{#each modals as modal}
  <Modal {modal} onOpen={openNewModal} onClose={closeModal} />
{/each}
