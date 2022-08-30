<script>
  import Motion from "svelte-motion/src/motion/MotionSSR.svelte";
  export let item;
  export let flipped;

  // const randomletter = (l) =>
  //   l
  //     .toString(36)
  //     .substring(7)
  //     .split("")
  //     .find((v) => isNaN(parseInt(v))) || "a";
  // $: l = (randomletter(item.r) + randomletter(item.g)).toUpperCase();
  const hangedtransform = (h) =>{
    if(item.hanged===1)
      return "hanged"
    else
      return "normal"
  }
  $: hanged = hangedtransform(item.hanged)
  flipped = false;
</script>
<main class:flipped on:click="{() => flipped = !flipped}">
  <Motion let:motion layoutId={item.id} layout>
    <div class="flip-card">
      <div class="flip-card-inner">
        <div use:motion class="flip-card-back" id={item.card_no}>
        </div>
        {#if flipped}
        <div use:motion class="flip-card-front" style="background: url('/card/{item.card_no}.jpeg'); background-size: contain; background-repeat: no-repeat;">
          <div style="font-size: 1rem; margin-top:100px;">
            {hanged}
            <!-- {item.card_no} -->
          </div>
        </div>
        {/if}
        
      </div>
    </div>
  </Motion>
</main>
<style>
  /* .item {
    width: 200px;
    height: 300px;
    color: white;
    font-size: large;
    background-color: transparent;
    perspective: 1000px;
    cursor: pointer;
    user-select: none;
    
  } */
  .flip-card {
    background-color: transparent;
    width: 180px;
    height: 300px;
    perspective: 1000px;
    cursor: pointer;
    user-select: none;
  }

  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.6s;
    transform-style: preserve-3d;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  }
  /* 
  .item-back{
    background-color: white;
    background: url('/back.jpg');
    background-size: contain;
    background-repeat: no-repeat;
    border-radius: 10px;
    
  }
  .item-front{
    background-color: white;
    background: url('/tarot-back.jpeg');
    background-size: contain;
    background-repeat: no-repeat;
    border-radius: 10px;
    
  } */
  .flipped .flip-card .flip-card-inner {
    transform: rotateY(180deg);
  }

  .flip-card-front,
  .flip-card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
  }

  .flip-card-back {
    background-color: #bbb;
    color: black;
    background: url('/back.jpg');
    background-size: contain;
    background-repeat: no-repeat;
    border-radius: 10px;
  }

  .flip-card-front {
    background-color: #2980b9;
    color: black;
    font-weight: bold;
    border-radius: 10px;
    transform: rotateY(180deg);
    
  }
</style>
