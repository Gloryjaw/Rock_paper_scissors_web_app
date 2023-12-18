<script>
	import Header from "./components/Header.svelte"
	import Usergame from "./components/Usergame.svelte";
	import Cpugame from "./components/Cpugame.svelte";

	let score = 0;
	let userTurn = true;
	let userInp;
	let showModal = false
	const handleInput = (e) =>{
		userInp = e.detail;
		userTurn = false
	}
	const handleWin = () =>{
		console.log(score)
		score = score +1
	}
</script>
{#if showModal}
<div class="rules">
	<p>RULES</p>
	
	<img src="./images/image-rules.svg" alt="">
	<button on:click={()=>{showModal = false}}><img src="./images/icon-close.svg" alt=""></button>
</div>

{/if}
<main>

<Header {score}/>
{#if userTurn}
<Usergame on:inp = {handleInput}/>
{:else}
<Cpugame {userInp} on:win = {handleWin} on:click = {()=>{userTurn = true}}/>
{/if}
<button class="rules_btn" on:click={()=>{showModal = true}}>RULES</button>
</main>


<style>
	main{
		width: 90%;
		max-width: 550px;
		height: 100%;
	    margin: auto;
		position: relative;
	}
	.rules_btn{
		color: white;
		background-color: transparent;
		border: 2px solid white;
		position: absolute;
		bottom: 0;
		left: 50%;
		transform: translateX(-50%);
		padding: 0.8em 3em;
		border-radius: 10px;
		letter-spacing: 3px;
	}
	.rules{
		background-color: white;
		position: absolute;
		width: 100%;
		height: 100%;
		z-index: 10;
		top: 0;
		left: 0;
		padding: 5em 0;
	}
	.rules>button{
		background-color: white;
		border: none;
		position: absolute;
		bottom: 50px;
		left: 50%;
		transform: translateX(-50%);
	}
	.rules>img{
		margin: auto;
		margin-top: 3em;
	}
	.rules>p{
		text-align: center;
		color: var(--dark-text);
		font-size: 1.5rem;
		font-weight: 700;
	}	
	@media (min-width : 1000px){
		main{

			width: 100%;
			max-width: none;
		}
		.rules_btn{
			left: 100%;
			bottom: 4%;
			
			transform: translateX(-120%);
		}
		main{
			position: static;
		}
		.rules{
			width: 30%;
			height: auto;
			left: 50%;
			top: 50%;
			transform: translate(-50%, -50%);
			border-radius: 10px;
			padding: 2em 2em;

		}
		.rules>img{
			width: 100%;
			margin: 0;
		}
		.rules>button{
			bottom: auto;
			top: 20px;
			left: 90%;

		}
		.rules>p{
			margin-bottom: 2em;
			text-align: left;
		}
	}
</style>