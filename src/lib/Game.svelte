<script>
  import Motion from "svelte-motion/src/motion/MotionSSR.svelte";
  import AnimateSharedLayout from "svelte-motion/src/components/AnimateSharedLayout/AnimateSharedLayout.svelte";
  import Item from "./Item.svelte";
  let card = 1;
  let flipped = false;
  let list = Array(card)
    .fill()
    .map((_, i) => {
      const r = Math.random(),
        g = Math.random(),
        b = Math.random(),
        card_no = Math.floor(Math.random() * 2), // 0 or 1
        hanged = Math.floor(Math.random() * 2);
      const t = (r + g + b) / 255;
      return {
        r: r / t,
        g: g / t,
        b: b / t,
        i: i,
        card_no: card_no,
        hanged: hanged,
      };
    })
    .sort((x, y) => x.r - y.r);
  const sort = (t) => {
    list = list.sort((x, y) => x[t] - y[t]);
  };

  let by = 1;
  $: sort(by % 3 === 1 ? "r" : by % 3 === 0 ? "b" : "g");
  let gap = 20;
  function shuffle() {
    flipped = false;
    by++;
    card = 4
    console.log(card)
    list = Array(card)
      .fill()
      .map((_, i) => {
        const r = Math.random(),
          g = Math.random(),
          b = Math.random(),
          card_no = Math.floor(Math.random() * 2),
          hanged = Math.floor(Math.random() * 2);
        const t = (r + g + b) / 255;
        return {
          r: r / t,
          g: g / t,
          b: b / t,
          i: i,
          card_no: card_no,
          hanged: hanged,
        };
      });
  }
</script>

<div class="background">
  <AnimateSharedLayout type="crossfade">
    <Motion let:motion={grid} layout>
      <div use:grid class="container" style="grid-gap: {gap}px; grid-template-columns: repeat({card}, 1fr);">
        {#each list as item (item.i)}
          <Item {item} {flipped} />
        {/each}
      </div>
    </Motion>
  </AnimateSharedLayout>
  <button on:click={shuffle}>shuffle</button>
</div>

<style>
  :global(*) {
    box-sizing: border-box;
  }

  .background {
    display: flex;
    flex-direction: column;
    height: 100%;
    justify-content: center;
    align-items: center;
    position: relative;
    overflow: hidden;
    flex-wrap: wrap;
  }
  .container {
    display: grid;
    align-items: center;
    justify-items: center; /* adjusted */
    /* grid-template-columns: repeat(card, 1fr); */
  }

  button {
    border: 4px solid black;
    background-color: transparent;
    color: black;
    border-radius: 4rem;
    padding: 1rem 2rem;
    font-size: 200%;
    margin-top: 10px;
  }
</style>
