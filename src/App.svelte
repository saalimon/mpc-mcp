<script>
  import { scrollTo, scrollRef, scrollTop } from "svelte-scrolling";
  import Game from "./lib/Game.svelte";
  import Landing from "./lib/Landing.svelte";
  import Prophecy from "./lib/Prophecy.svelte";
  import data from "./data.json";
  let cardList = [];
  let cards = [];
  const navItems = [
    { label: "HOME", href: "home" },
    { label: "GUIDE", href: "guide" },
    { label: "AUGUR", href: "augur" },
    // { label: "FRAME", href: "frame" },
    { label: "TALK", href: "talk" },
  ];
  function prophecy() {
    if (cardList.length === 4) {
      cards = cardList.map((e) => {
        return data["card"].find((el) => {
          return parseInt(el.cardId) === parseInt(e.card_no);
        });
      });
    }
  }
  $: cardList, prophecy();
</script>

<nav>
  <div class="inner">
    <ul class="navbar-list">
      {#each navItems as item}
        <li>
          <a use:scrollTo={{ ref: item.href, duration: 1000 }} href={item.href}
            >{item.label}</a
          >
        </li>
      {/each}
    </ul>
  </div>
</nav>
<div class="content">
  <section use:scrollRef={"home"}>
    <div class="section">
      <div class="splash  splash-img-home">
        <div class="center-content">
          <img src="logo.png" alt="logo" class="logo" />
          <h1 class="title" style="opacity: 100% !important;">
            MONSTER CARDS PROJECT
          </h1>
          <a href="https://twitter.com/hashtag/MPC_MCP" class="twitter"
            >#MPC_MCP</a
          >
        </div>
        <h4 class="footer">
          *นี่เป็นกิจกรรมที่จัดขึ้นภายในคอมมูมอนสเตอร์พรอมเท่านั้น(MPC)*<br />
          *ผู้เข้าชมที่มาจากภายนอก ขอความร่วมมือ ไม่ฟลอโล่ว ไม่รีทวิต ไม่โควททวิต
          หรือไม่กดเฟปทวิตของผู้เล่นในคอมมูนี้อย่างเด็ดขาด ขอบคุณที่ให้ความร่วมมือ*
        </h4>
      </div>
    </div>
  </section>

  <section use:scrollRef={"guide"}>
    <div class="section">
      <div class="splash splash-img-guide">
        <div class="center-content">
          <h1 class="title" style="color: white;">GUIDE TO AUGUR</h1>
          <a
            href="https://reidberlin.wixsite.com/mpc-mcp?fbclid=IwAR18AhyRZf5JcuxpwgrWSIkO4Vzu733yVyJwMXVYEvv7ur4plY_i88rUtjY"
          >
            <img src="MCP_W.png" alt="logo" class="logo" />
          </a>
          <p class="content-font" style="font-size: 20px;">
            ทำนายดวงชะตาของคุณในวันนี้ โดยเมื่อทำการเลือกไพ่ออกมาสี่ใบ <br />
            โดยที่จะเรียงคำทำนายในด้าน การงาน สุขภาพ ความรัก และโชคลาภ ตามลำดับ
          </p>
          <p class="content-font" style="font-size: 12px;">
            *นี่เป็นกิจกรรมที่จัดเพื่อความบันเทิงเท่านั้น
            โปรดใช้วิจารณญาณในการรับชม*
          </p>
        </div>
      </div>
    </div>
  </section>
  <section use:scrollRef={"augur"}>
    <div class="section" style="background-color: salmon;">
      <div class="splash splash-img">
        <Game bind:cardList />
      </div>
    </div>
  </section>
  <section use:scrollRef={"result"}>
    {#if cardList.length == 4}
      <div class="section-100 summary-section">
        <div class="splash ">
          <h2 class="title" style="opacity: 100% !important;">
            The Prophcey Result
          </h2>
          <div class="flex-container">
            <Prophecy prophecy={cards[0]} hanged={cardList[0].hanged} />
            <Prophecy prophecy={cards[1]} hanged={cardList[1].hanged} />
            <Prophecy prophecy={cards[2]} hanged={cardList[2].hanged} />
            <Prophecy prophecy={cards[3]} hanged={cardList[3].hanged} />
          </div>
        </div>
      </div>
    {/if}
  </section>

  <!-- <section use:scrollRef={"test"}>
    <Prophecy prophecy={test} />
  </section> -->
  <section use:scrollRef={"talk"}>
    <div class="splash-img-talk">

      <Landing name="talk" />
    </div>
  </section>
</div>

<button class="corner" on:click={() => scrollTop()}>Go to top</button>

<style>
  .flex-container {
    display: flex;
    flex-direction: row;
  }
  .content {
    height: 100%;
    display: grid;
    grid-template-rows: 1fr;
    grid-template-columns: 1fr;
  }
  .section {
    width: 100%;
    position: relative;
  }
  .section-100 {
    height: 100%;
    width: 100%;
    position: relative;
  }

  .summary-section {
    background: rgba(0, 0, 0, 0.8) url("/splash3.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-blend-mode: darken;
  }
  .splash {
    padding: 100px;
    height: auto;
    width: 100%;
    text-align: center;
    display: flex;
    justify-content: center; /* align horizontal */
    align-items: center; /* align vertical */
    flex-direction: column;
    min-height: 100vh;
  }
  .logo {
    width: 167px;
    height: 167px;
    object-fit: cover;
  }
  .title {
    font-family: droid-serif, serif;
    font-weight: 400;
    font-style: normal;
    font-size: 68px;
  }
  .content-font {
    font-family: "Nunito", sans-serif;
    font-size: 19px;
    color: inherit;
  }
  .twitter {
    font-family: "Nunito", sans-serif;
    font-size: 19px;
    color: inherit;
  }
  .footer {
    margin-top: auto;
    font-family: "Nunito", sans-serif;
    font-size: 12px;
  }
  .center-content {
    margin: auto auto;
  }
  .splash-img {
    background: rgba(0, 0, 0, 0.7) url("/splash5.jpeg");
    background-size: cover;
    background-repeat: no-repeat;
    background-blend-mode: darken;
  }
  .corner {
    position: fixed;
    right: 0;
    bottom: 0;
    opacity: 40%;
  }
  .corner:hover {
    opacity: 80%;
  }

  .splash-img-talk {
    background: rgba(0, 0, 0, 0.0) url("/splash6.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-blend-mode: darken;
  }

  @media (max-width: 900px) {
   .splash {
    padding: 40px;
   }
   .flex-container {
    display: flex;
    flex-direction: column;
  }
  }
</style>
