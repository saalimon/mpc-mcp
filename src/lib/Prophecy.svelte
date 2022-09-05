<script>
    export let prophecy;

</script>
  
  <main>
    <div class="panel">
        <div style="color: black">
            <div>
                <p>{prophecy['cardName']}</p>
            </div>
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
    .panel{
        background-color: whitesmoke;
        height: 90vh;
        width: 90%;
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
  