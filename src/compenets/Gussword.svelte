<script>
import { text } from "svelte/internal";
    export let seconds;
    export let won;
    export let mot = "";
    export let last = "";
    export let failCount = 0;
    $: console.log(mot)
    let guessMot;
    let blank = [];
    $: processMot(mot);
    $: prosesletre(last);

    const processMot = (mot) => {
        blank = Array(mot.length).fill("_");
        console.log(blank);
        guessMot = blank.toString().replaceAll(",", " ");
    };

    const prosesletre = (l) => {
        if (l != "") {
            let i = 0;
            let liste = mot.split("");

            let found = false;

            while (i < mot.length) {
                if (liste[i].toUpperCase() == l.toUpperCase()) {
                    found = true;
                    blank[i] = l;
                }
                i++;
            }

            if (!found) {
                failCount += 1;

            }

            guessMot = blank.toString().replaceAll(",", " ");
            if (!blank.includes("_")){
                won = true
            }
        }
    };
</script>

<p>
    {#if seconds == false}
        The word is {mot}
        {:else}
        {guessMot}
    {/if}
</p>

<style>
    p {
        font-size: 3em;
        margin: 0;
        margin-top: 1%;
    }
</style>
