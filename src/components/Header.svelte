<script>
    export let score;
</script>

<div class="score_container">
    <img class="logo" src="./images/logo.svg" alt="rock_paper_scissor_logo">
    <div class="score_card">
        <p id="score">SCORE</p>
        <p id="score_value">{score}</p>
    </div>
</div>

<style>
    .score_container{
        display: flex;
        width:100%;
        max-width: 550px;
        justify-content: space-between;
        border: 3.5px solid var(--header-outline);
        padding: 0.7em;
        border-radius: 5px;
        margin: auto;
    }
    .score_card{
        background-color: white;
        width: 30%;
        text-align: center;
        padding: 0.5em 0;
        border-radius: 4px;
        
    }
    #score{
        color: var(--score-text);
        font-size: 0.65rem;
        letter-spacing: 1.5px;
    }
    #score_value{
        color: var(--dark-text);
        font-size: 2rem;
        font-weight: 700;
    }
    .logo{
        width: 30%;
        align-self: center;
    }
    @media(min-width: 650px){
        #score{
            font-size: 0.8rem;
        }
        #score_value{
            font-size: 2.8rem;
        }
    }
</style>