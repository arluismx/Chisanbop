<script>
    let velocidad = $state(1000);
    let operaciones = $state(5);
    let valorabs = $state(10);

    let numbers = $state([0]);

    

    function iniciale() {
        numbers = [0]
        for (let i = 0; i < operaciones; i++) {
            let total = numbers.reduce(
                (accumulator, currentValue) => accumulator + currentValue,0);
            const rndInt = Math.floor(Math.random() * valorabs) + 1
            if ((total - rndInt) > 0){
                numbers.push(rndInt * (Math.random() < 0.5 ? -1 : 1))
            }
            else{
                numbers.push(rndInt)
            }
        }
        alert(numbers)
    }


</script>


<div>
    <button onclick={iniciale}>iniciar</button>
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
    p{
        display: inline;
    }
    .mm{
        width: 2rem;
        height: 2rem;
        border: solid 1px;
    }
    button{
        border: solid 1px;
    }
</style>