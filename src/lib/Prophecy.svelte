<script>
  export let prophecy;
  export let hanged;
</script>

<main>
  <div class="panel">
    <div style="color: black">
      <div>
        <div class="flip-card" style="margin: 0 auto;">
          <div class="flip-card-inner">
            <div class="flip-card-back" />
            <div
              class="flip-card-front"
              style="background: url('/mpc-mcp/card/{prophecy.cardId}.png'); 
                                                background-size: contain;
                                                background-repeat: no-repeat;
                                               "
            />
          </div>
        </div>
        <h2>{prophecy["cardName"]}</h2>
        {#if hanged && prophecy["isHaveProphecyHanged"]}
          <p class="remark">
            <strong
              >เนื่องจากคุณได้รับไพ่ใบนี้แบบกลับหัว
              ดังนั้นความหมายของคำทำนายจะเป็นดังต่อไปนี้</strong
            >
          </p>
          <p>
            <strong>การงาน</strong> - {prophecy["hangedProphecy"]["working"]}
          </p>
          <p>
            <strong>สุขภาพ</strong> - {prophecy["hangedProphecy"]["health"]}
          </p>
          <p><strong>ความรัก</strong> - {prophecy["hangedProphecy"]["love"]}</p>
          <p>
            <strong>การเงิน</strong> - {prophecy["hangedProphecy"]["money"]}
          </p>
        {:else if hanged && prophecy.isHaveProphecyHanged == false && prophecy.cardId == 77}
          <p class="remark">
            <strong
              >หากไพ่นี้กลับด้าน การงาน
              การสุขภาพและความรักของคุณจะตรงกันข้ามและถูกผู้ที่มีอำนาจในด้านนั้นๆควบคุมอยู่
              ส่วนสำหรับการเงินและโชคลาภจะดีอย่างราวกับตกไปในขุมทรัพย์แห่งชีวิต</strong
            >
          </p>
          <p><strong>การงาน</strong> - {prophecy["prophecy"]["working"]}</p>
          <p><strong>สุขภาพ</strong> - {prophecy["prophecy"]["health"]}</p>
          <p><strong>ความรัก</strong> - {prophecy["prophecy"]["love"]}</p>
          <p><strong>การเงิน</strong> - {prophecy["prophecy"]["money"]}</p>
        {:else if hanged && prophecy.isHaveProphecyHanged == false}
          <p class="remark">
            <strong
              >เนื่องจากคุณได้รับไพ่ใบนี้แบบกลับหัว
              ดังนั้นความหมายของคำทำนายจะตรงข้าม</strong
            >
          </p>
          <p><strong>การงาน</strong> - {prophecy["prophecy"]["working"]}</p>
          <p><strong>สุขภาพ</strong> - {prophecy["prophecy"]["health"]}</p>
          <p><strong>ความรัก</strong> - {prophecy["prophecy"]["love"]}</p>
          <p><strong>การเงิน</strong> - {prophecy["prophecy"]["money"]}</p>
        {:else}
          <p>
            <strong>คำทำนายของไพ่ใบนี้จะเป็นดังต่อไปนี้</strong>
          </p>
          <p><strong>การงาน</strong> - {prophecy["prophecy"]["working"]}</p>
          <p><strong>สุขภาพ</strong> - {prophecy["prophecy"]["health"]}</p>
          <p><strong>ความรัก</strong> - {prophecy["prophecy"]["love"]}</p>
          <p><strong>การเงิน</strong> - {prophecy["prophecy"]["money"]}</p>
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
    height: auto;
  }
  .panel {
    background-color: whitesmoke;
    padding: 4%;
    width: 20vw;
    border-radius: 10px;
    margin: 0 auto;
    display: flex;
  }

  .remark {
    color: #ff3e00;
  }

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
    background: url("/back.jpg");
    background-size: contain;
    background-repeat: no-repeat;
    border-radius: 10px;
  }

  .flip-card-front {
    background-color: #bbb;
    color: black;
    background: url("/card/1.png");
    background-size: contain;
    background-repeat: no-repeat;
    border-radius: 10px;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  @media (max-width: 400px) {
    .panel {
      width: auto;
    }
  }

  @media (max-width: 900px) {
    .panel {
      width: auto;
    }
  }
</style>
