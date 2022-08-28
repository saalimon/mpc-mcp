<script>
  import { scrollTo, scrollRef, scrollTop } from "svelte-scrolling";
  import Game from "./lib/Game.svelte";
  import Landing from "./lib/Landing.svelte";

  const navItems = [
    { label: "HOME", href: "home" },
    { label: "AUGUR", href: "angur" },
    { label: "CARDS", href: "cards" },
    { label: "FRAME", href: "frame" },
    { label: "TALK", href: "talk" },
  ];
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
      <div class="splash  splash-img">
        <div class="center-content">
          <img src="/logo.png" alt="logo" class="logo" />
          <h1 class="title" style="opacity: 100% !important;">MONSTER CARDS PROJECT</h1>
          <a href="https://twitter.com/hashtag/MPC_MCP" class="twitter"
            >#MPC_MCP</a
          >
        </div>
        <h4 class="footer">
          *นี่เป็นกิจกรรมที่จัดขึ้นภายในคอมมูมอนสเตอร์พรอมเท่านั้น(MPC)
          ผู้เข้าชมที่มาจากภายนอก ขอความร่วมมือ ไม่ฟลอโล่ว ไม่รีทวิต ไม่โควททวิต
          หรือไม่กดเฟปทวิตของผู้เล่นในคอมมูนี้อย่างเด็ดขาด
          ขอบคุณที่ให้ความร่วมมือ*
        </h4>
      </div>
    </div>
  </section>

  <section use:scrollRef={"angur"}>
    <div class="section" style="background-color: #808080;">
      <div class="splash">
        <div class="center-content">
          <h1 class="title" style="color: white;">ANGUR</h1>
          <img src="/MCP_W.png" alt="logo" class="logo" />
          <p class="content-font" style="font-size: 20px;">
            มาทำนายดวงชะตาของคุณวันนี้กัน
          </p>
          <p class="content-font" style="font-size: 12px;">
            *นี่เป็นกิจกรรมที่จัดเพื่อความบันเทิงเท่านั้น
            โปรดใช้วิจารณญาณในการรับชม*
          </p>
        </div>
      </div>
    </div>
  </section>
  <section use:scrollRef={"cards"}>
    <Game />
  </section>
  <section use:scrollRef={"frame"}>
    <Landing name="frame" />
  </section>
  <section use:scrollRef={"talk"}>
    <Landing name="talk" />
  </section>
</div>

<button on:click={() => scrollTop()}>Go to top</button>

<style>
  .content {
    height: 100%;
    display: grid;
    grid-template-rows: 1fr;
    grid-template-columns: 1fr;
  }
  .section {
    height: 100vh;
    width: 100%;
    position: relative;
  }
  .splash {
    height: 100%;
    width: 100%;
    text-align: center;
    display: flex;
    justify-content: center; /* align horizontal */
    align-items: center; /* align vertical */
    flex-direction: column;
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
    /* background: rgba(0, 151, 19, 0.3); */
    background-size: cover;
    background-repeat: no-repeat;
    background-color: rgba(0, 0, 0);
    /* z-index: 2; */
    opacity: 60%;
    background-image: url("/splash1.jpg");
    /* background: linear-gradient(rgba(255,255,255,.5), rgba(255,255,255,.5)), url('/splash1.jpg'); */

  }
</style>
