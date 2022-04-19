<script>
  let color1 = '#B3FEFF';
  let color2 = '#DD33FF';

  let deg = 0;

  function upDeg(){
    deg += 1;
  }

  function downDeg(){
    deg -= 1;
  }
  
  var hex = ["0","1","2","3","4","5","6","7","8","9"
                 ,"A","B","C","D","E","F"];

  let hexCode = [];
  let hexCode2 = [];
      
  function hexRan(){
    hexCode = [];
    hexCode2 = [];
    hexCode.push("#");
    hexCode2.push("#");
    for(let i = 0; i < 6; i++){
      function random_hex(hex){
        return hex[Math.floor(Math.random()*hex.length)];
      }
      hexCode.push(random_hex(hex));
      hexCode2.push(random_hex(hex));
    }
    color1 = hexCode.join("");
    color2 = hexCode2.join("");
  }
  
</script>

<main>
  <div class="colorPicker">
    <div class="colorCircle">
      <input type="color" class="colorBar" id="colorBar1" bind:value={color1}/>
    </div>
    <label for="colorBar1">{color1}</label>
  </div>
  
  <div class="circle" style="
    background: linear-gradient({deg}deg, {color2}, {color1});
  ">
    <input type="range" class="degRange" id="degRange" min="0" max="360" bind:value={deg}/>
    <div class="degValue">
      <input type="number" class="degInput" id="degInput" min="
        
        0" max="360" bind:value={deg}/>
    </div>
    <div class="degBall" style="
      transform: rotate({deg}deg);
      ">
      <div class="ball"></div>
    </div>
    <button class="randomBtn" on:click="{hexRan}">Random</button>
  </div>

  
  
  <div class="colorPicker">
    <div class="colorCircle">
      <input type="color" class="colorBar" id="colorBar2" bind:value={color2}/>
    </div>
    <label for="colorBar2">{color2}</label>
  </div>
</main>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');
  
  :root{
    --font-1920: 1.4vw;
    --font-768: 4.4vw;
    --font-color: #7d7d7d;
  }
  
  *, *::before, *::after{
		box-sizing: border-box;
    padding: 0;
    margin: 0;
    font-family: 'Roboto', sans-serif;
	}

  :global(body){
    box-sizing: border-box;
    padding: 0;
    margin: 0;
    background: #F5FFFD;
  }

  main{
    box-sizing: border-box;
    padding: 0;
    margin: 0;
    width: 100%;
    height: 100vh;
    display: grid;
    justify-content: center;
    align-items: center;
    align-content: center;
    justify-items: center;
    grid-template-columns: auto;
    grid-template-rows: auto auto auto;
    grid-gap: 2em;
  }

  div.circle{
    position: relative;
    border-radius: 50%;
    width: 30vw;
    height: 30vw;
    box-shadow: 0px 2vw 3vw rgba(0, 0, 0, 0.15),
                0px -2vw 3vw rgba(255, 255, 255, 1);
  }

  input[type="number"].degInput{
    position: relative;
    background: transparent;
    border: none;
    outline: none;
    padding: 1vw;

    width: 15vw;

    font-size: var(--font-1920);
    color: #3b3b3b;
    font-weight: 400;
    text-align: center;
  }

  input[type=number].degInput::-webkit-inner-spin-button {
    -webkit-appearance: none;
  }
  
  .degValue{
    position: absolute;
    bottom: 2.5%;
    right: 15%;
    width: 5.5vw;
    height: 5.5vw;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;

    background: rgba(255, 255, 255, 0.22);
    backdrop-filter: blur(0.65vh);
    border: 1px solid (255, 255, 255, 0.5);
    box-shadow: 0px 0.55vw 1vw rgba(0, 0, 0, 0.15);
  }

  .degRange{
    position: absolute;
    width: 7vw;
    height: 1vw;

    border: none;
    outline: none;

    transform: rotate(-90deg);

    z-index: 999;
    cursor: pointer;

    bottom: 9.5%;
    right: -2%;

    -webkit-appearance: none;
    border-radius: 1vw;
    box-shadow: -1vw 0 1.5vw rgba(0, 0, 0, 0.25);
    background: rgba(255, 255, 255, 0.2);
    backdrop-filter: blur(0.65vh);
    border: 1px solid (255, 255, 255, 0.5);
  }

  .degRange::-webkit-slider-thumb {
    
    -webkit-appearance: none;
    appearance: none;
    
    width: 0.75vw;
    height: 2vw;
    border-radius: 1vw;
    
    box-shadow: -1vw 0 1.5vw rgba(0, 0, 0, 0.25);
    background: rgba(0, 0, 0, 0.85);
    backdrop-filter: blur(0.65vh);
    border: 1px solid (255, 255, 255, 0.5);
    
    cursor: pointer;
  }

  div.degBall{
    position: absolute;
    bottom: 0%;
    left: 74.25%;
    
    width: 1vw;
    height: 6.75vw;

    display: flex;
    justify-content: center;
    align-items: flex-start;
  }

  div.degBall .ball{
    width: 1vw;
    height: 1vw;

    border-radius: 50%;

    background: #eee;
    box-shadow: 0 1vw 1.5vw rgba(0, 0, 0, 0.35);
  }
  
  div.colorPicker{
    width: 15vw;
    height: 4vw;

    background: #fff;
    
    display: grid;
    justify-content: center;
    align-items: center;
    align-content: center;
    grid-template-columns: auto 50%;

    overflow: hidden;

    box-shadow: 0 1vw 1.5vw rgba(0, 0, 0, 0.25);
    border-radius: 1vw;
  } 

  input[type="color"].colorBar {
    position: relative;
    top: -50%;
    left: -50%;
    transform: transition(50%, 50%);
    -webkit-appearance: none;
    border: none;
    background: transparent;

    width: 6vw;
    height: 6vw;
  }
  
  input[type="color"].colorBar::-webkit-color-swatch {
    border-radius: 50%;
    border: none;
  }
  
  label{
    font-size: var(--font-1920);
    color: var(--font-color);
    font-weight: 400;
    text-transform: uppercase;
  }

  button.randomBtn{
    position: absolute;
    top: 15%;
    left: -10%;
    padding: 1vw 3vw;
    
    border: none;
    border-radius: 1vw;
    
    outline: none;
    
    background: rgba(255, 255, 255, 0.22);
    backdrop-filter: blur(0.65vh);
    border: 1px solid (255, 255, 255, 0.5);
    box-shadow: 0px 0.55vw 1vw rgba(0, 0, 0, 0.15);

    font-weight: 300;
    font-size: calc(var(--font-1920) - 0.25vw);
    color: #4F4F4F;

    cursor: pointer;
    transition: all 0.25s ease;
  }

  button.randomBtn:hover{
    padding: 2vw 3vw;
    background: rgba(255, 255, 255, 0.85);
    transition: all 0.25s ease;
  }

  /* ----- Reesponsive ----- */
  @media screen and (max-width: 768px) {
    main{
      grid-gap: 1.5em;
    }
    
    div.circle{
      width: 75vw;
      height: 75vw;
    }
  
    input[type="color"].colorBar{
      width: 20vw;
      height: 20vw;
    }

    div.colorPicker{
      width: 45vw;
      height: 15vw;
      
      border-radius: 4vw;
    }

    label{
      font-size: var(--font-768);
    }

    input[type="number"].degInput{
      position: relative;
      padding: 2vw;
  
      width: 35vw;
  
      font-size: var(--font-768);
    }
    
    .degValue{
      position: absolute;
      bottom: 2%;
      right: 15%;
      width: 15vw;
      height: 15vw;
    }
  
    .degRange{
      position: absolute;
      width: 20vw;
      height: 2vw;
  
      bottom: 10.5%;
      right: -2%;
    }

  .degRange::-webkit-slider-thumb {
    
    width: 2.25vw;
    height: 4.5vw;
  }

    div.degBall{
      position: absolute;
      bottom: 1.25%;
      left: 74.25%;
      
      width: 1vw;
      height: 16vw;
  
      display: flex;
      justify-content: center;
      align-items: flex-start;
    }
  
    div.degBall .ball{
      transform: scale(2.5);
    }

    button.randomBtn{
      position: absolute;
      top: 15%;
      left: -10%;
      padding: 3vw 10vw;
      
      border-radius: 4vw;
      
      font-size: calc(var(--font-768) - 0.25vw);
    }

    button.randomBtn:hover{
      padding: 6vw 10vw;
    }
  }
</style>