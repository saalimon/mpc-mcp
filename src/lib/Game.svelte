<script>
  // @ts-nocheck

  // import Motion from "svelte-motion/src/motion/MotionSSR.svelte";
  // import AnimateSharedLayout from "svelte-motion/src/components/AnimateSharedLayout/AnimateSharedLayout.svelte";
  import Item from "./Item.svelte";
  import { flip } from "svelte/animate";
  export let cardList = [];
  let card = 1; // initial card for each turn
  let flipped = false;
  let cardNo = 196; // number of tarot card
  let rerender = true;

  function arrCard(num) {
    const nums = new Set();
    while (nums.size !== 8) {
      nums.add(Math.floor(Math.random() * num));
    }
    const card_list = [...nums];
    return Array(card)
      .fill()
      .map((_, i) => {
        let r = Math.random(),
          g = Math.random(),
          b = Math.random(),
          card_no = card_list[i], // 0 or 1
          hanged = Math.floor(Math.random() * 2);
        const t = (r + g + b) / 255;
        nums.add(card_no);
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
  }
  let list = arrCard(cardNo);
  const sort = (t) => {
    list = list.sort((x, y) => x[t] - y[t]);
  };

  let by = 1;
  $: sort(by % 3 === 1 ? "r" : by % 3 === 0 ? "b" : "g");
  let gap = 20;
  function shuffle() {
    flipped = false;
    by++;
    card = 4;
    list = arrCard(cardNo);
    rerender = !rerender;
    cardList = [];
  }

  function reset() {
    flipped = false;
    by++;
    card = 1;
    list = arrCard(cardNo);
    rerender = !rerender;
    cardList = [];
  }
</script>

<main>
<div class="background">
  <!-- <AnimateSharedLayout type="crossfade"> -->
  <!-- <Motion let:motion={grid} layout> -->

  <h1 class="title">Augur Your Fortune</h1>
  <div
    class="container"
    style="grid-gap: {gap}px; grid-template-columns: repeat({card}, 1fr);"
  >
    <!-- {#key rerender} -->
    {#each list as item (item.i)}
      <div animate:flip={{ duration: 500 }}>
        {#key rerender}
          <Item bind:cardList {item} {flipped} />
        {/key}
      </div>
    {/each}
    <!-- {/key} -->
  </div>

  <!-- </Motion> -->
  <!-- </AnimateSharedLayout> -->
  <button class="raise" on:click={ cardList.length ==4 ? reset : shuffle} >{ cardList.length ==4 ? "Reveal Again" : "Reveal your cards"}</button>
</div>
</main>

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

  h1 {
    margin-top: 0;
    margin-bottom: 100px;
  }

  button {
    background-color: #ff2e8d;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    color: white;
    border-radius: 4rem;
    padding: 1rem 2rem;
    font-size: 150%;
    margin-top: 80px;
    transition: 0.25s;
  }
  button:hover,
  button:focus {
    border-color: var(--hover);
    color: white;
  }
  .raise:hover,
  .raise:focus {
    box-shadow: 0 0.5em 0.5em -0.4em var(--hover);
    transform: translateY(-0.25em);
  }
  main {
    text-align: center;
    max-width: 240px;
    margin: 0 auto;
  }
  @media (min-width: 640px) {
    main {
      max-width: none;
    }
    .title {
      font-size: 3.2em;
    }
  }

  @media (max-width: 640px) {
    main {
      max-width: none;
    }
    .title {
      font-size: 3.2em;
    }
  }
</style>
