<script>
  let numbas = $state(0)
  let velocidad = $state(1000);
  let operaciones = $state(5);
  let valorabs = $state(10);
  let numbers = $state([0]);
  let elapsed = 0;
  let intervalId;
  let respcm1 = $state(0);
  let respcm2 = $state(0);
  let respcm3 = $state(0);
  let totalote = $state(0);
  

  function iniciale() {
      numbers = [0]
      respcm1 = 0
      respcm2 = 0
      respcm3 = 0
      for (let i = 0; i < operaciones; i++) {
          let total = numbers.reduce(
              (accumulator, currentValue) => accumulator + currentValue,0);
          const rndInt = Math.floor(Math.random() * valorabs) + 1
          if ((total - rndInt) >= 0){
              numbers.push(rndInt * (Math.random() < 0.5 ? -1 : 1))
          }
          else{
              numbers.push(rndInt)
          }
      }
      console.log(numbers)
      if (!intervalId) {
        let contador = 0
        intervalId = setInterval(()=>{
          numbas = numbers[contador]
          contador += 1;
          if (contador == numbers.length){
            clearInterval(intervalId);
            // release our intervalId from the variable
            intervalId = null;
            let sum = 0;
            numbers.forEach( num => {
              sum += num;
            })
            totalote = sum;
            if (Math.random() < 0.5){
              respcm1 = sum;
              respcm2 = Math.floor(Math.random() * ((operaciones*valorabs) - 0 + 1)) + 0;
              respcm3 = Math.floor(Math.random() * ((operaciones*valorabs) - 0 + 1)) + 0;
            }
            else {
              if (Math.random() < 0.5){
                respcm1 = Math.floor(Math.random() * ((operaciones*valorabs) - 0 + 1)) + 0;
                respcm2 = sum;
                respcm3 = Math.floor(Math.random() * ((operaciones*valorabs) - 0 + 1)) + 0;
            }
            else {
              respcm1 = Math.floor(Math.random() * ((operaciones*valorabs) - 0 + 1)) + 0;
              respcm2 = Math.floor(Math.random() * ((operaciones*valorabs) - 0 + 1)) + 0;
              respcm3 = sum;
            }
            }
          }
        }, 1000);
      }
  }

  function ganasteoke1(){
    if (totalote == respcm1){
      alert("SI")
    }
    else{
      alert("NO")
    }
  }
  function ganasteoke2(){
    if (totalote == respcm2){
      alert("SI")
    }
    else{
      alert("NO")
    }
  }
  function ganasteoke3(){
    if (totalote == respcm3){
      alert("SI")
    }
    else{
      alert("NO")
    }
  }
</script>

<h1>
  {numbas}
</h1>
<div>
  <button class="cm" onclick={ganasteoke1}>
      {respcm1}
  </button>
  <button class="cm" onclick={ganasteoke2}>
      {respcm2}
  </button>
  <button class="cm" onclick={ganasteoke3}>
      {respcm3}
  </button>
</div>
<div>
  <button class="ctdr" onclick={iniciale}>iniciar</button>
  <p style="margin-right: 1rem;"></p>
  <p>Velocidad: {velocidad}</p>
  <button class="mm">
      +
  </button>
  <button class="mm">
      -
  </button>
  <p style="margin-right: 1rem;"></p>
  <p>Operaciones: {operaciones}</p>
  <button class="mm">
      +
  </button>
  <button class="mm">
      -
  </button>
  <p style="margin-right: 1rem;"></p>
  <p>Valor Absoluto: {valorabs}</p>
  <button class="mm">
      +
  </button>
  <button class="mm">
      -
  </button>
</div>


<style>  
  h1 {
      background: transparent;
      color: white;
      font-weight: bold;
      font-size: 18rem;
      margin: 0%;
  }
  .cm {
        font-size: 3rem;
        border: transparent;
    }
    p{
        display: inline;
    }
    .mm{
        width: 2rem;
        height: 2rem;
        border: solid 1px;
    }
    .ctdr{
        border: solid 1px;
    }
</style>