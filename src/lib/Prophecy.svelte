<script>
  export let prophecy;
</script>

<main>
  <div class="panel">
    <div style="color: black">
      <div>
        <p>{prophecy["cardName"]}</p>
        <div class="flip-card">
          <div class="flip-card-inner">
            <div class="flip-card-front" style="background: url('/card/{prophecy["cardId"]}.png'); 
                                                background-size: contain;
                                                background-repeat: no-repeat;
                                               ">
            </div>
          </div>
        </div>
    </div>
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }
  .panel {
    background-color: whitesmoke;
    height: 90vh;
    width: 90%;
    border-radius: 10px;
    margin: 0 auto;
    display: flex;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  .flip-card {
    margin: 24px 40px;
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
    border-radius: 10px;
  }

  .flip-card-front {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    border-radius: 10px;
  }


  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
