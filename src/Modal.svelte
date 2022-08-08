<script>
  export let message = "default";
  export let showModal = false;
  export let isPromo = false;
</script>

{#if showModal === true}
  <div on:click>
    <p class:promo={isPromo}>{message}</p>
    <slot />
  </div>
{/if}

<style>
  .promo {
    color: red;
  }
</style>
