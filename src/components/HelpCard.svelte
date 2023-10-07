<script lang="ts">
  export let card_id: string;
  export let active_id: string;
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div class="help-card" id={card_id}>
  <div class="help-card-top">
    <!-- next do nothing line to suppress spurious warning -->
    {#if false} <slot />{/if}

    <slot name="topic" />
    <button id={card_id} class="open"> &#10133; </button>
  </div>
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  {#if active_id === card_id}
    <div class="help-card-btm">
      <slot name="description" />
      <button id={card_id} class="close">&#10060;</button>
    </div>
  {/if}
</div>

<style>
  .help-card {
    padding: 8px;
    margin: 16px;
    /* width: 80%; */
    /* border: 2px solid blue; */
    border-radius: 8px;
    box-shadow: 5px 10px 8px #888888;
  }

  .help-card-top {
    display: grid;
    grid-template-columns: 10fr 1fr;
    /* border-bottom: 2px solid blue; */
    color: white;
    background-color: blue;
    border-radius: 8px;
    padding: 8px;
  }

  .help-card-btm {
    display: grid;
    grid-template-columns: 10fr 1fr;
    background-color: lightsalmon;
    padding: 12px;
    border-radius: 8px;
  }

  .open,
  .close {
    background-color: white;
    color: red;
    display: flex;
    justify-content: center;
    /* border: 2px solid black; */
    align-items: center;
  }
</style>
