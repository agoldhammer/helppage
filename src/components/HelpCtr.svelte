<script lang="ts">
  import HelpCard from "./HelpCard.svelte";
  type MouseEvent = { currentTarget: HTMLDivElement };
  const topic1 = "Mollit magna commodo laborum aute.";
  const topic2 =
    "Deserunt adipisicing occaecat incididunt ullamco occaecat fugiat culpa nisi.";
  const topic3 =
    "Incididunt ullamco adipisicing excepteur laboris id consectetur dolor.";
  const topics = [topic1, topic2, topic3];
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
  <HelpCard>
    <p slot="topic">HELP I need somebody</p>
    <p slot="description">Not just anybody</p>
  </HelpCard>
  {#each topics as topic}
    <HelpCard>
      <p slot="topic">{topic}</p>
      <p slot="description">
        Ut labore ex sint id excepteur. Cillum anim et ex consequat veniam nulla
        est ea enim excepteur voluptate. Non officia esse velit sit non
        cupidatat quis proident aute laborum sint. Qui excepteur tempor cillum
        laboris est est.
      </p>
      />
    </HelpCard>
  {/each}
</div>

<style>
  .help-ctr {
    height: 100vh;
    border: 2px solid red;
    border-radius: 8px;
    overflow-y: scroll;
  }
</style>
