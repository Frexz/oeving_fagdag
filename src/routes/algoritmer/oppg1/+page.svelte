<script>
    import OppgaveLayout from "../../../komponenter/OppgaveLayout.svelte";
    let n = 1
    let sekvens

    function collatz(n) {
        sekvens = [n]
        while (n > 1) {
            let forrigeTall = sekvens[-1]

            if (forrigeTall % 2 == 0) {
                sekvens.push(forrigeTall * 2)
            } else {
                sekvens.push((forrigeTall * 3) + 1)
            }
        }
    }

    $: {
        collatz(n)
    }

</script>

<OppgaveLayout>
    <div class="tekst" slot="tekst">
        <h1>Oppgave 1</h1>
        <p>
            I matematikken finnes det et uløst problem som kalles Collatz’ Formodning. 
            Formodningen sier at hvis man har et positivt naturlig tall skal man følge et sett 
            med enkle steg og man vil alltid ende opp med tallet 1 før eller siden. Stegene er som følger:
            Gitt et naturlig tall n, gjør følgende:
        </p>
            <ul>
                <li>Hvis tallet er et partall, del det på 2</li>
                <li>Hvis tallet er et oddetall, gang det med 3 og pluss på 1</li>
                <li>Gjenta prosessen til man ender opp med 1</li>
            </ul>
        <p>
            F.eks hvis man begynner med tallet 5 får man 5→16→8→4→2→1<br><br>
            Skriv et program som tar imot et tall n fra brukeren og som skriver ut Collatz-sekvensen 
            for tallet og antall steg i sekvensen. Sekvensen i eksempelet ovenfor har 5 steg.

        </p>
    </div>

    <div class="oppgave" slot="oppgave">
        <h2>Velg et tall n</h2>
        <input type="number" bind:value={n} style="margin-bottom:50px;">

        <h2>Collatz-sekvensen til {n}</h2>
        <p style="font-size: 20px;">
            {#each sekvens as num}
                {num}&rarr;
            {/each}
        </p>
    </div>
</OppgaveLayout>