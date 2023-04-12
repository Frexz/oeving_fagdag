<script>
    export let gamePlaying
    export let land

<<<<<<< HEAD

    let score = 0
    let questionCount = 0
    let isFinished
    let hasAnswered
    let lives = ["heart", "heart", "heart"]
    let questions = []
    let alternatives = []

    function initializeGame() {
        isFinished = false
        hasAnswered = false
        score = 0
        lives = ["heart", "heart", "heart"]
        makeQuestions(10)
        nextQuestion()
=======
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
        
>>>>>>> 5ae374eb67e4ed1ea7ed48a164aaf596465cf5a5
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

<<<<<<< HEAD
        let unsorted = temp.map((country) => {
            if (country === questions[questionCount - 1]) {
                return {"country": country, "correct": true, "color": 'green'}
            } else {
                return {"country": country, "correct": false, "color": 'red'}
            }
        })

        let i = Math.floor(Math.random()*unsorted.length)

        while (unsorted.length > 0) {
            alternatives.push(unsorted.splice(i, 1)[0])
            i = Math.floor(Math.random()*unsorted.length)
        }
    }

    function nextQuestion() {
        questionCount++
        makeAlternatives()
    }

    async function checkAnswer(answer) {
        hasAnswered = true

        if (answer.correct) {
            score += 100
        } else {
            let i = lives.length - 1

            while (lives[i] === "broken-heart") {
                i--

                if (i < 0) {
                    isFinished = true
                    return
                }
            }

            lives[i] = "broken-heart"
        }

        await sleep(2000);
        
        if (questionCount == questions.length || !lives.includes("heart")) {
            isFinished = true
            return
        }

        alternatives = []
        hasAnswered = false
        nextQuestion()
    }

    function sleep(ms) {
        return new Promise(resolve => setTimeout(resolve, ms))
    }

    $: {
        if (gamePlaying) {
            initializeGame()
        }
    }

    $: {
        if (isFinished) {
            gamePlaying = false
=======
        let i = Math.floor(Math.random()*temp.length)

        while (temp.length > 0) {
            alternatives.push(temp.splice(i, 1)[0])
            i = Math.floor(Math.random()*temp.length)
        }
    }


    $: {
        if (gamePlaying) {
            runGame()
>>>>>>> 5ae374eb67e4ed1ea7ed48a164aaf596465cf5a5
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
<<<<<<< HEAD
            {#each alternatives as alt, i}
                <button class="alt-button" on:click={() => {checkAnswer(alt)}} style="background-color: {(hasAnswered) ? alt.color : "transparent"}">{alt.country.name}</button>
=======
            {#each alternatives as alt}
                <button class="alt-button">{alt.name}</button>
>>>>>>> 5ae374eb67e4ed1ea7ed48a164aaf596465cf5a5
            {/each}
        </div>
    </div>
</div>