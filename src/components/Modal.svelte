<script>
  /**
   *@stopPropagation - stop the event bubbling or capturing any further
   *@capture - fires the handler during the capture phase not bubbling
   *@once - makes sure the event can only fire once (removes handler)
   *@preventDefault - prevent the default action (run e.preventDefault())
   *@self - only fires the event if the clicked element is the target
   */

  // Props
  export let isPromo = false
  export let showModal = false
</script>

{#if showModal}
  <div class="backdrop" class:promo={isPromo} on:click|self>
    <div class="modal">
      <slot />
    </div>
  </div>
{/if}

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    background: rgba(0, 0, 0, 0.8);
  }
  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: #fff;
  }
  .promo .modal {
    background: crimson;
    color: white;
  }
</style>
