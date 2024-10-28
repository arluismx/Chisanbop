<script>
    import { handlers } from "svelte/legacy";

    let arreglo = $state([0,4,6,7,-9])
    let numbas = $state(1)
    let velocidad = $state(1);
    let interval = $state(2000);
    let count = $state(0)
    let coleccion = $state([0])
    /*
    $effect(() => {
        const id = setInterval(() => {
            numbas = Math.floor(Math.random() * (10 - 1) + 1)
        }, interval);

        return () => {
            clearInterval(id);
        };
    });
    */

    function iterea() {
        
    }

    function randomea() {
        if (count == 0) {
            const id = setInterval(() => {
                numbas = Math.floor(Math.random() * (10 - 1) + 1)
                count = 1
            }, interval);

            return () => {
                clearInterval(id);
            };
        }
        
        
    }

</script>

<h1>
    {numbas}
</h1>
<div>
    <button >
        5
    </button>
    <button >
        5
    </button>
    <button >
        5
    </button>
</div>

<style>
    

    h1 {
        /*
        text-align: center;
        border: solid;
        height: 1vh;
        width: 100%;*/
        background: transparent;
        color: white;
        font-weight: bold;
        font-size: 18rem;
        margin: 0%;
    }
</style>