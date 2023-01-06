<script>
  export let prophecy;
  export let hanged;
</script>

<main>
  <div class="panel">
    <div style="color: black">
      <div>
        <h2>{prophecy["cardName"]}</h2>
        {#if hanged && prophecy["isHaveProphecyHanged"]}
          <p><strong>การงาน</strong>{prophecy["hangedProphecy"]["working"]}</p>
          <p><strong>สุขภาพ</strong>{prophecy["hangedProphecy"]["health"]}</p>
          <p><strong>ความรัก</strong>{prophecy["hangedProphecy"]["love"]}</p>
          <p><strong>การเเงิน</strong>{prophecy["hangedProphecy"]["money"]}</p>
        {:else}
          <p><strong>การงาน</strong> {prophecy["prophecy"]["working"]}</p>
          <p><strong>สุขภาพ</strong>{prophecy["prophecy"]["health"]}</p>
          <p><strong>ความรัก</strong>{prophecy["prophecy"]["love"]}</p>
          <p><strong>การเเงิน</strong>{prophecy["prophecy"]["money"]}</p>
        {/if}
      </div>
    </div>
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    /* max-width: 240px; */
    margin: 0 auto;
  }
  .panel {
    background-color: whitesmoke;
    height: 20vh;
    width: 20vw;
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

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
