<script lang="ts">
  import HelpCard from "./HelpCard.svelte";
  import { helpitems } from "$lib/topics";
  import { writable } from "svelte/store";
  import { fly, fade } from "svelte/transition";
  const active_id_store = writable("");

  function hdlClick(e: MouseEvent) {
    // console.log("clicked", e.target);
    const target = e.target as HTMLButtonElement;
    const button_id = target.id || "";

    // console.log("setting active to id", button_id);
    const active_id = $active_id_store;
    if (active_id === button_id) {
      active_id_store.set("");
    } else {
      active_id_store.set(button_id);
    }
    // console.log("HelpCtr", e.currentTarget);
  }
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div class="help-ctr" on:click={hdlClick}>
  <h1>Help Topics</h1>
  {#each helpitems as helpitem}
    <HelpCard card_id={helpitem.id} active_id={$active_id_store}>
      <h2 slot="topic">{helpitem.topic}</h2>
      <p slot="description" transition:fade={{ duration: 500 }}>
        {helpitem.description}
      </p>
    </HelpCard>
  {/each}
</div>

<style>
  h1 {
    text-align: center;
  }
  .help-ctr {
    height: 100vh;
    /* border: 2px solid red; */
    border-radius: 8px;
    overflow-y: scroll;
  }
</style>
