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

<section use:scrollRef={"home"}>
  <Landing name="home" />
</section>
<section use:scrollRef={"angur"}>
  <Landing name="angur" />
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
<button on:click={() => scrollTop()}>Go to top</button>
