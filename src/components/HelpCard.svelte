<script lang="ts">
  //   type MouseEvent = { currentTarget: HTMLDivElement };
  function hdlClick(e: MouseEvent) {
    console.log("clicked", e.currentTarget);
    if (!e.currentTarget) {
      throw new Error("null target");
    } else {
      const clickSrc = e.currentTarget;
      console.log("clickSrc", clickSrc);
      const parent = clickSrc.parentElement;
      console.log("parent", parent);
    }

    // console.log("sibling", cardtop.nextSibling);
  }
</script>

<div class="help-card">
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div id="help-top-1" class="help-card-top">
    <!-- next do nothing line to suppress spurious warning -->
    {#if false} <slot />{/if}

    <slot name="topic" />
    <button id="help-open-1" class="open" on:click|capture={hdlClick}>
      &#10133;
    </button>
  </div>
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div id="help-btm-1" class="help-card-btm">
    <slot name="description" />
    <button class="close" on:click|capture={hdlClick}>&#10060;</button>
  </div>
</div>

<style>
  .help-card {
    padding: 8px;
    margin: 8px;
    width: 80%;
    border: 2px solid blue;
    border-radius: 8px;
  }

  .help-card-top {
    display: grid;
    grid-template-columns: 10fr 1fr;
    border-bottom: 2px solid blue;
    color: white;
    background-color: blue;
  }

  .help-card-btm {
    display: grid;
    grid-template-columns: 10fr 1fr;
    background-color: lightsalmon;
  }

  .open,
  .close {
    background-color: white;
    color: red;
    display: flex;
    justify-content: center;
    border: 2px solid black;
    align-items: center;
  }
</style>
