<script>
    export let userInp;
    import Gamebutton from "../shared/Gamebutton.svelte";
    import WinnerModule from "../shared/WinnerModule.svelte";
    import {scale} from "svelte/transition"
    let cpuBrain = ["rock", "paper", "scissors"]
    let cpuType = cpuBrain[Math.floor(Math.random()*3)];
    let cpuTurn = false
    let showWinner = false;
    let userWin = false;
    let tie = false
    if(userInp == cpuType){
        userWin = false
        tie = true;
    }
    else if(userInp == "rock"){
        if(cpuType == "paper"){
            userWin = false
        }
        else{
            userWin = true
        }
    }
    else if(userInp == "paper"){
        if(cpuType == "rock"){
            userWin = true
        }
        else{
            userWin = false;
        }
    }
    else if (userInp == "scissors"){
        if(cpuType == "rock"){
            userWin = false
        }
        else{
            userWin = true
        }
    }
    setTimeout(()=>{
        cpuTurn = true
    }, 1500)
    setTimeout(() => {
        showWinner = true;
    }, 2000);
</script>

<div class="cpu_container" >
    <div class="game_container">
        <div class="button_container user" in:scale = {{delay: 500, duration: 500}}>
            <div class="winner_container" class:win = {showWinner && userWin}>
                <Gamebutton type = {userInp} nonclickable = {true}/>
            </div>
            
            <p class="text user_text">YOU PICKED</p>
        </div>
        <div class="winner_section">
            {#if showWinner}
            <WinnerModule {userWin} {tie} on:win on:click/>
            {/if}
        </div>
        <div class="cpu_section">
            {#if cpuTurn}
            <div class="button_container cpu" in:scale = {{duration: 500}}>
                <div class="winner_container" class:win = {showWinner && !userWin && !tie}>
                    <Gamebutton type = {cpuType} nonclickable = {true}/>
                </div>
          
            </div>
            {:else}
            <div class="button_container empty">
                <div class="empty_container">
                    <div class="empty_button"></div>
                </div>
            </div>
            {/if}
            <p class="text cpu_text">THE HOUSE PICKED</p>
        </div>
    </div>

</div>

<style>
    .cpu_container{
        margin-top: 5em;

    }
    .game_container{
        display: flex;
        max-width: 700px;
        margin: auto;
        justify-content: center;
        gap: 80px;
    }
    .cpu_section{
        width: 100%;
        max-width: 250px;
    }
    .button_container{
        width: 100%;
        display: grid;
        place-items: center;
        max-width: 200px;

    }
    .winner_container{
        width: 100%;
        border-radius: 100%;
      
    }
    .winner_container.win{
        box-shadow: 0px 0px 0px 30px rgba(255, 255, 255, 0.066), 
                    0px 0px 0px 60px rgba(255, 255, 255, 0.033),
                    0px 0px 0px 90px rgba(255, 255, 255, 0.026);
    }
    .button_container.empty, .button_container.cpu{
        margin: auto;
    }

    .empty_container{
        width: 100%;
        height: 0;
        padding-bottom: min(100%, 250px);
        border-radius: 100%;
        position: relative;
        max-width: 250px;
    }
    .empty_button{
        width: 80%;
        height: 0;
        padding-bottom: 80%;
        border-radius: 100%;
        background-color:  hsl(214, 48%, 16%);
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }
    .text{
        font-size: calc(0.5rem + 1.2vw);
        margin-top: 2.5em;
        text-align: center;
        color: white;
        font-weight: 700;
        letter-spacing: 2px;
    }
    .winner_section{
        position: absolute;
        bottom: 100px;
    }
    @media (min-width: 1000px){
        .winner_section{
            position: static;

        }
        .game_container{
            gap: 30px;
        }
    }
</style>