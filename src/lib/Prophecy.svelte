<script>
  import LayoutGrid, { Cell } from "@smui/layout-grid";
  export let prophecy;
  export let postion; // told user about [ working | health | money | love]
</script>

<main>
  <div class="panel">
    <div class="prophecy">
      <LayoutGrid>
        <Cell>
          <div class="cell">
            <Cell span={6}>
              <div class="flip-card">
                <div class="flip-card-inner">
                  <div
                    class="flip-card-front"
                    style="background: url('/card/{prophecy['cardId']}.png'); 
                                                    background-size: contain;
                                                    background-repeat: no-repeat;
                                                   "
                  />
                </div>
              </div>
            </Cell>
            <Cell span={4}>
              <div class="cell">
                <div class="desc">
                   <!-- show all the prophcey but will do as one prophecy -->
                  <h2>คุณได้รับไพ่ {prophecy["cardName"]}</h2>
                  <p>ด้านการงาน : {prophecy.prophecy["working"]}</p>
                  <p>ด้านการสขภาพ : {prophecy.prophecy["health"]}</p>
                  <p>ด้านการความรัก : {prophecy.prophecy["love"]}</p>
                  <p>ด้านการโชคลาภ : {prophecy.prophecy["money"]}</p>
                  
                  <!-- show remark if the card is hanged and don't have the specifiy phophecy -->
                  <!-- {#if prophecy["isHaveProphecyHanged"] == false && flipped == true} 
                  <p class="remark">แต่คุณได้รับไพ่ใบนี้แบบกลับหัว ดังนั้นคำทำนายจะให้ผลตรงกันข้าม</p>
                  {/if} -->

                </div>
              </div>
            </Cell>
          </div>
        </Cell>
      </LayoutGrid>
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

  .prophecy {
    color: black;
    width: 100%;
    margin: 40px;
  }

  .cell {
    display: flex;
    justify-content: center;
    align-items: top;
  }

  .desc {
    margin: 24px 40px;
    text-align: left;
    color: black;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  .remark {
color: red;
  }

  .flip-card {
    margin: 24px 40px;
    background-color: transparent;
    width: 360px;
    height: 600px;
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
