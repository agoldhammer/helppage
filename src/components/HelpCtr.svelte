<script lang="ts">
  type MouseEvent = { currentTarget: HTMLDivElement };
  function hdlClick(e: MouseEvent) {
    console.log("clicked", e.currentTarget);
    if (!e.currentTarget) {
      throw new Error("null target");
    } else {
      const clickSrc = e.currentTarget;
      console.log("clickSrc", clickSrc);
      const parentElement = clickSrc.parentElement;
      console.log("parent", parent);
    }

    // console.log("sibling", cardtop.nextSibling);
  }
</script>

<div class="help-ctr">
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->

  <div class="help-card">
    <div id="help-top-1" class="help-card-top">
      <p>HELP I need somebody</p>
      <div class="open" on:click|capture={hdlClick}>&#10133;</div>
    </div>
    <div id="help-btm-1" class="help-card-btm">
      <p>not just anybody</p>
      <div class="close">&#10060;</div>
    </div>
  </div>
</div>

<style>
  .help-ctr {
    height: 100vh;
    border: 2px solid red;
    border-radius: 8px;
  }

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
  }

  .help-card-btm {
    display: grid;
    grid-template-columns: 10fr 1fr;
  }

  .open,
  .close {
    display: flex;
    justify-content: center;
    border: 2px solid black;
    align-items: center;
  }
</style>
