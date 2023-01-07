<script>
  export let name;
</script>

<main>
  <div class="panel">
    <h1>{name}</h1>
    <p>
      สวัสดีค่ะ นับเป็นการจัดกิจกรรมในมู MPC ของเราเลย
      ด้วยความชอบพวกงานกิจกรรมวาดไพ่มาก
      ก็เลยดีใจมากๆเลยค่ะที่มีคนมาร่วมกิจกรรมเยอะขนาดนี้ ขอบคุณทุกคนมากๆเลยนะคะ!
      ดีใจมากๆเลย เราจะพยายามทำออกมาให้ดีที่สุดเพื่อทุกคนนะคะ อาจจะมีผิดพลาดบ้าง
      จะด้วยการสื่อสารหรือตัวกิจกรรมเอง ก็ต้องขออภัยด้วยน้าY///Y
    </p>

    <p>
      ถ้าหากสงสัยอะไร สามารถติดต่อได้ที่ <br> ทางทวิตเตอร์ <a
        href="https://twitter.com/MPC_DnD">@MPC_DnD</a
      >
      | ทางเฟสบุ๊ค
      <a href="https://www.facebook.com/aksrapuck.klinhrom"
        >Aksrapuck Klinhrom</a
      >
    <br> ทางทวิตเตอร์ <a href="https://twitter.com/mpc_rhoda">@mpc_rhoda</a> |
      ทางเฟสบุ๊ค
      <a href="https://www.facebook.com/maya.silsangwon">Maya Silsangwon</a> <br> สุดท้ายนี้ขอบคุณมากนะคะ
      รักชาว MPC ที่สุดเลย ♥︎
    </p>
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  h1 {
    color: black;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
    text-decoration: underline;
  }

  p {
    color: black;
  }

  .panel {
    background-color: white;
    padding: 4% 30%;
    border-radius: 10px;
    margin: 100px;
    display: flex;
    flex-direction: column;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
  @media (max-width: 900px) {
    .panel {
    margin: 40px;
    padding: 4% ;
   
  }
 
}
</style>
