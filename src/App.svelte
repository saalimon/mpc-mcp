<script>
  import { scrollTo, scrollRef, scrollTop } from "svelte-scrolling";
  import Game from "./lib/Game.svelte";
  import Landing from "./lib/Landing.svelte";
  import Prophecy from "./lib/Prophecy.svelte";
  import data from "./data.json";
  let cardList = [];
  let cards = [];
  let test = {
    cardId: "0",
    cardName: "THE INVASION",
    isHaveProphecyHanged: true,
    prophecy: {
      working:
        "จะเกิดปัญหาที่ผ่านพ้นไปได้ค่อนข้างลำบาก เพราะจะมีคู่แข่งมาขัดขวางการทำงาน และคุณได้เจอกับการเปลี่ยนแปลงครั้งใหญ่ในหน้าที่การงาน",
      health:
        "โปรดระวังตัวไว้ เพราะจะคุณจะเป็นโรคภัยไข้เจ็บ หากมีโรคประจําตัวอยู่แล้วก็อาจจะมีโรคอื่นๆเพิ่มมาอีก",
      love: "จะมีบุคคลที่เข้ามาหาคุณ หากคุณยังไม่มีคู่ คนๆนั้นจะมาเป็นคู่ของคุณ และเขาจะเป็นตัวแปรสำคัญ ในการเปลี่ยนชีวิตการเป็นอยู่ของคุณ หากคุณมีคู่แล้ว ไพ่ใบนี้จะหมายถึงจะมีบุคคลที่สาม เข้ามาสร้างอุปสรรค เป็นแบบทดสอบ ให้ความสัมพันธ์ของคุณ",
      money:
        "เกิดการเปลี่ยนผันทางการเงินของคุณ ในทางที่ดี แต่ก็ต้องแลกกับบางสิ่งที่จะไม่เหมือนเดิมต่อไป",
    },
    hangedProphecy: {
      working:
        "จะเป็นไปได้ราบรื่นเพราะจะมีคนคนหนึ่งมาเปลี่ยนแปลงการทำงานของคุณ",
      health: "วางใจได้ สุขภาพของคุณเป็นปกติดี ไม่มีอาการแทรกซ้อน",
      love: "ยังต้องรอต่อไป แต่เขาคนนั้นมาแน่หากคุณมีคู่แล้ว ผู้มาเยือนในความหมายไพ่ใบนี้จะหมายถึง ญาติผู้ใหญ่คนใกล้ตัวมามีส่วนร่วมช่วยผลักดันความรักของคุณ",
      money:
        "เกิดการเปลี่ยนผันทางการเงินของคุณ ในทางที่ไม่ดีนัก แต่คุณจะได้ของสำคัญในชีวิตกลับมา",
    },
  };
  const navItems = [
    { label: "HOME", href: "home" },
    { label: "GUIDE", href: "guide" },
    { label: "AUGUR", href: "augur" },
    { label: "FRAME", href: "frame" },
    { label: "TALK", href: "talk" },
  ];
  function prophecy() {
    if (cardList.length === 4) {
      cards = cardList.map((e) => {
        return data["card"].find((el) => {
          return el.cardId === e;
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
          *นี่เป็นกิจกรรมที่จัดขึ้นภายในคอมมูมอนสเตอร์พรอมเท่านั้น(MPC)*<br>
          *ผู้เข้าชมที่มาจากภายนอก ขอความร่วมมือ ไม่ฟลอโล่ว ไม่รีทวิต ไม่โควททวิต
          หรือไม่กดเฟปทวิตของผู้เล่นในคอมมูนี้อย่างเด็ดขาด
          ขอบคุณที่ให้ความร่วมมือ*
        </h4>
      </div>
    </div>
  </section>

  <section use:scrollRef={"guide"}>
    <div class="section" style="background-color: #808080;">
      <div class="splash splash-img-guide">
        <div class="center-content">
          <h1 class="title" style="color: white;">GUIDE TO AUGUR</h1>
          <img src="MCP_W.png" alt="logo" class="logo" />
          <p class="content-font" style="font-size: 20px;">
            ทำนายดวงชะตาของคุณในวันนี้ โดยเมื่อทำการเลือกไพ่ออกมาสี่ใบ <br>
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
    <div class="section" style="background-color: rgba(0, 0, 0, 0.4);">
      <Game bind:cardList />
    </div>
  </section>
  <section use:scrollRef={"prophecy"}>
    {#if cardList.length == 4}
      <p>{cardList[0]}</p>
      <Prophecy prophecy={cards[0]} />
    {/if}
  </section>

  <section use:scrollRef={"test"}>
    <Prophecy prophecy={test} />
  </section>
  <section use:scrollRef={"frame"}>
    <Landing name="frame" />
  </section>
  <section use:scrollRef={"talk"}>
    <Landing name="talk" />
  </section>
</div>

<button class="corner" on:click={() => scrollTop()}>Go to top</button>

<style>
</style>
