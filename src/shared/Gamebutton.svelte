<script>
    export let type;
    export let nonclickable = false;
    import {createEventDispatcher} from 'svelte'
    let dispatch = createEventDispatcher();
    const handleClick = () =>{
        if(nonclickable == false){
            dispatch("inp", type)
        }
        
    }
</script>




<button disabled = {nonclickable} on:click = {handleClick} class="outer_button" class:rock = {type == "rock"} class:paper = {type == "paper"} class:scissor = {type == "scissors"}>
    <div class="inner_button">
        <img src="./images/icon-{type}.svg" alt="">
    </div>
</button>



<style>

    button:focus{
        box-shadow: none;
        transform: translate(5px, 6px);
    }
    .outer_button{
        border: none;
        border-radius: 100%;
        width: 100%;
        height: 0;
        padding-bottom: min(100%, 200px);
        position: relative;
        display: block;
        max-width: 200px;
    }

    .inner_button{
        background-color: white;
        width: 80%;
        height: 0;
        padding-bottom: 80%;
        border-radius: 100%;
        position: absolute;
       left: 50%;
       top: 50%;
       transform: translate(-50%, -50%);
        box-shadow: inset 2px 4px 3px rgba(0, 0, 0, 0.29);
    }
    img{
        width: 50%;
        position: absolute;
        left: 50%;
       top: 50%;
       transform: translate(-50%, -50%);

    }
    .rock{
        margin: auto;
        background-image: linear-gradient(to bottom, var(--rock-gradient-top), var(--rock-gradient-bottom));
        box-shadow: 1px 5px 0px rgba(160, 38, 38, 0.771);
    }
    .paper{
        background-image: linear-gradient(to bottom, var(--paper-gradient-top), var(--paper-gradient-bottom));
        box-shadow: 1px 5px 0px rgba(57, 57, 246, 0.656);
    }
    .scissor{
        background-image: linear-gradient(to bottom, var(--scissor-gradient-top), var(--scissor-gradient-bottom));
        box-shadow: 1px 5px 0px hsl(40, 78%, 34%);
    }
</style>