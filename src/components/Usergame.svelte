<script>
    import Gamebutton from "../shared/Gamebutton.svelte";

</script>

<div class="game_container">
    <div class="top_row">
        <div class="button_container">
            <Gamebutton on:inp type = "paper"/>
        </div>
        <div class="button_container">
            <Gamebutton on:inp type = "scissors"/>
        </div>


    </div>
    <div class="bottom_row">
        <div class="button_container rock">
            <Gamebutton on:inp type = "rock"/>
        </div>

    </div>


</div>


<style>
    .game_container{
        width: 100%;
        margin: auto;
        margin-top: 5em;
        position: relative;
        padding: 6px;
        background-image: url(../images/bg-triangle.svg);
        background-size: 70% 70%;
        background-position: center;
        background-repeat: no-repeat;
        max-width: 600px;
        
    }

    .top_row{
        display: flex;
        justify-content: space-between;

    }
    .bottom_row{
        margin-top: 1em;
    }
    .button_container{
        width: 40%;
        max-width: 200px;

    }
    .button_container.rock{
        margin: auto;
       
    }

</style>