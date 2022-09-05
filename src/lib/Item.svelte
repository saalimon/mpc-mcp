<script>
  // import Motion from "svelte-motion/src/motion/MotionSSR.svelte";
  export let item;
  export let flipped;
  export let cardList = []
  const hangedtransform = (h) =>{
    if(item.hanged===1)
      return "transform: rotateX(180deg);"
    else
      return "transform: rotateY(180deg);"
  }
  $: hanged = hangedtransform(item.hanged)
  flipped = false;
  function getCard(){
    flipped = !flipped
    cardList = [...cardList, String(item.card_no) ]
  }
</script>

<main class:flipped on:click="{getCard}">
    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-back">
        </div>
        <div class="flip-card-front" style="background: url('/card/{item.card_no}.png'); 
                                            background-size: contain;
                                            background-repeat: no-repeat;
                                            {hangedtransform(item.hanged)};">
        </div>
        
      </div>
    </div>
</main>
<style>
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
    background-color: #bbb;
    color: black;
    background: url('/card/1.png');
    background-size: contain;
    background-repeat: no-repeat;
    border-radius: 10px;
    
  }
</style>
