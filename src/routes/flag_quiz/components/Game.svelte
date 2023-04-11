<script>
    export let gamePlaying
    export let land

    let score = 0
    let lives = ["heart", "heart", "heart"]
    let questionCount = 0
    let questions = []
    let alternatives = []

    function runGame() {
        score = 0
        lives = ["heart", "heart", "heart"]
        makeQuestions(10)
        questionCount++
        makeAlternatives()
        
    }

    function makeQuestions(n){
        for (let i = 0; i < n; i++) {
            let randomCountry = land[Math.floor(Math.random()*land.length)]
            
            while(questions.includes(randomCountry)) {
                randomCountry = land[Math.floor(Math.random()*land.length)]
            }

            questions.push(randomCountry)
        }
        
    }

    function makeAlternatives() {
        let temp = []
        temp.push(questions[questionCount - 1])

        while (temp.length < 4) {
            let randomAlt = land[Math.floor(Math.random()*land.length)]
            
            while (alternatives.includes(randomAlt)) {
                randomAlt = land[Math.floor(Math.random()*land.length)]
            }

            temp.push(randomAlt)
        }

        let i = Math.floor(Math.random()*temp.length)

        while (temp.length > 0) {
            alternatives.push(temp.splice(i, 1)[0])
            i = Math.floor(Math.random()*temp.length)
        }
    }


    $: {
        if (gamePlaying) {
            runGame()
        }
    }
</script>

<div class="game-area">
    <div class="dashboard">
        <div class="lives">
            {#each lives as status}
                <img class="life" src="/img/{status}.png" alt="heart" style="filter: {(status === 'broken-heart') ? 'grayscale(100%)' : 'none'}">
            {/each}
        </div>

        <div class="timer">
            <h1>Timer Placeholder</h1>
        </div>

        <div class="score-area">
            <div class="score">
                <h2>Score: <span style="margin-left: 20px;">{score}</span></h2>
            </div>

            <div class="question-tracker">
                <h2>{questionCount}<span style="margin: 0 10px;">/</span>{questions.length}</h2>
            </div>
        </div>
    </div>
    
    <div class="questions">

        <div class="flag-box">
            <img class="flag" src="{questions[questionCount - 1].file_url}" alt="flag_{questionCount}">
        </div>
        

        <div class="alternatives">
            {#each alternatives as alt}
                <button class="alt-button">{alt.name}</button>
            {/each}
        </div>
    </div>
</div>