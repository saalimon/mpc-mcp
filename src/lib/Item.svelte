<script>
  import Motion from "svelte-motion/src/motion/MotionSSR.svelte";
  export let item;

  const randomletter = (l) =>
    l
      .toString(36)
      .substring(7)
      .split("")
      .find((v) => isNaN(parseInt(v))) || "a";
  $: l = (randomletter(item.r) + randomletter(item.g)).toUpperCase();
</script>

<Motion let:motion layoutId={item.id} layout>
  <div use:motion class="item">
    <!-- style={`background-color:rgb(${item.r},${item.g},${item.b})`} -->
    {l}
  </div>
</Motion>

<style>
  .item {
    width: 100px;
    height: 150px;
    color: black;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 30px;
    font-weight: 900;
    background-color: whitesmoke;
  }
</style>
