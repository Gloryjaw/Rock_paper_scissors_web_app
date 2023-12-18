<script>
export let userWin = true;
export let tie;
import {scale} from "svelte/transition"
import { createEventDispatcher , onMount} from "svelte";
let dispatch = createEventDispatcher()

onMount(()=>{
    if(userWin){
        dispatch("win")
    }
})
</script>

<div class = "winner_module" in:scale = {{duration : 500}}>
    {#if tie}
        <p>TIE</p>
    {:else if userWin}
        <p>YOU WIN</p> 
    {:else}
        <p>YOU LOSE</p> 
    {/if}
    <button on:click>PLAY AGAIN</button>
</div>

<style>
    .winner_module{
        width: 100%;
        margin: auto;
        margin-top: 4em;
    }
    .winner_module>p{
        color: white;
        font-size: 3rem;
        font-weight: 700;
        text-align: center;
        margin-bottom: 0.2em;
    }
    button{
        display: block;
        padding: 1em 3.5em;
        margin: auto;
        color: var(--dark-text);
        letter-spacing: 2px;
    }
    button:hover{
        color: red;
        background-color: white;
        outline: none;
        border-radius: 3px;
        border: none;
    }
    @media (min-width: 1000px){
        .winner_module{
            min-width: 250px;
        }
    }
</style>