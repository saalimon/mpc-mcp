<script>
  export let prophecy;
  export let hanged;
  export let order = 0;

  function displayProphecy(hanged, order) {
    let checkHanged =
      hanged && prophecy.isHaveProphecyHanged == true
        ? "hangedProphecy"
        : "prophecy";
    if (order === 0) {
      return `<p>
          <strong>การงาน</strong> - ${prophecy[checkHanged]["working"]}
        </p>`;
    } else if (order === 1) {
      return `<p>
          <strong>สุขภาพ</strong> - ${prophecy[checkHanged]["health"]}
        </p>`;
    } else if (order === 2) {
      return `<p><strong>ความรัก</strong> - ${prophecy[checkHanged]["love"]}
        </p>`;
    } else {
      return `<p>
          <strong>โชคลาภ</strong> - ${prophecy[checkHanged]["money"]}
        </p>`;
    }
  }
</script>

<main>
  <div class="panel">
    <div class="details">
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
        <div class="desc">
          <h2>{prophecy["cardName"]}</h2>
          {#if hanged && prophecy["isHaveProphecyHanged"]}
            <p class="remark">
              <strong
                >เนื่องจากคุณได้รับไพ่ใบนี้แบบกลับหัว
                ดังนั้นความหมายของคำทำนายจะเป็นดังต่อไปนี้</strong
              >
            </p>
            {@html displayProphecy(hanged, order)}
          {:else if hanged && prophecy.isHaveProphecyHanged == false && prophecy.cardId == 63}
            <p class="remark">
              <strong
                >เนื่องจากคุณได้รับไพ่ใบนี้แบบกลับหัว
                ดังนั้นความหมายของคำทำนายจะเป็นดังต่อไปนี้</strong
              >
            </p>
            {@html displayProphecy(hanged, order)}
            <p class="remark">
              <strong
                >note: ไพ่ใบนี้ไม่มีความหมายเป็นพิเศษเวลากลับหัวหากจับได้ใบเดียว
                เเต่หากจับได้ร่วมกับใบอื่น
                ให้นำเอาความหมายของไพ่เหล่านันในเชิงกลับหัวมาร่วมตีความด้วย</strong
              >
            </p>
          {:else if hanged && prophecy.isHaveProphecyHanged == false && prophecy.cardId == 77}
            <p class="remark">
              <strong
                >หากไพ่นี้กลับด้าน การงาน
                การสุขภาพและความรักของคุณจะตรงกันข้ามและถูกผู้ที่มีอำนาจในด้านนั้นๆควบคุมอยู่
                ส่วนสำหรับการเงินและโชคลาภจะดีอย่างราวกับตกไปในขุมทรัพย์แห่งชีวิต</strong
              >
            </p>
            {@html displayProphecy(hanged, order)}
          {:else if hanged && prophecy.isHaveProphecyHanged == false}
            <p class="remark">
              <strong
                >เนื่องจากคุณได้รับไพ่ใบนี้แบบกลับหัว
                ดังนั้นความหมายของคำทำนายจะให้ผลตรงข้าม</strong
              >
            </p>
            {@html displayProphecy(hanged, order)}
          {:else}
            <p>
              <strong>คำทำนายของไพ่ใบนี้จะเป็นดังต่อไปนี้</strong>
            </p>
            {@html displayProphecy(hanged, order)}
          {/if}
        </div>
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
  .details {
    color: black;
  }
  .desc {
    padding-left: 0px;
    padding-right: 0px;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  @media (max-width: 500px) {
    .panel {
      width: auto;
      justify-content: center;
    }
  }

  @media (max-width: 1000px) {
    .panel {
      width: auto;
      justify-content: center;
    }
    .details {
      min-width: 760px;
    }
    .desc {
      padding-left: 40px;
      padding-right: 40px;
    }
  }
</style>
