<script>
  // @ts-nocheck

  // import Motion from "svelte-motion/src/motion/MotionSSR.svelte";
  // import AnimateSharedLayout from "svelte-motion/src/components/AnimateSharedLayout/AnimateSharedLayout.svelte";
  import Item from "./Item.svelte";
  import { flip } from "svelte/animate";
  import Particles from "svelte-particles";
  import { loadFull } from "tsparticles";

  import Landing from "./Landing.svelte";

  export let cardList = [];
  let card = 1; // initial card for each turn
  let flipped = false;
  let cardNo = 89; // number of tarot card
  let rerender = true;

  let particlesConfig = {
    particles: {
      color: {
        value: "#000",
      },
      links: {
        enable: true,
        color: "#000",
      },
      move: {
        enable: true,
      },
    },
  };

  let onParticlesLoaded = (event) => {
    const particlesContainer = event.detail.particles;

    // you can use particlesContainer to call all the Container class
    // (from the core library) methods like play, pause, refresh, start, stop
  };

  let particlesInit = async (main) => {
    // you can use main to customize the tsParticles instance adding presets or custom shapes
    // this loads the tsparticles package bundle, it's the easiest method for getting everything ready
    // starting from v2 you can add only the features you need reducing the bundle size
    await loadFull(main);
  };

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
</script>

<div class="background">
  <Particles
  id="tsparticles"
  options="{particlesConfig}"
  on:particlesLoaded="{onParticlesLoaded}"
  particlesInit="{particlesInit}"
/>
  <div
    class="container"
    style="grid-gap: {gap}px; grid-template-columns: repeat({card}, 1fr);"
  >
    {#each list as item (item.i)}
      <div animate:flip={{ duration: 500 }}>
        {#key rerender}
          <Item bind:cardList {item} {flipped} />
        {/key}
      </div>
    {/each}
  </div>
  <button on:click={shuffle}>Reveal your cards</button>
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
    /* border: 4px solid black; */
    background-color: #ff2e8d;
    /* background-color: transparent; */
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    color: white;
    border-radius: 4rem;
    padding: 1rem 2rem;
    font-size: 150%;
    margin-top: 80px;
  }
</style>
