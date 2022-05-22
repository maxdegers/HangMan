<!-- npm run dev -->
<script>
	import { onMount, text } from "svelte/internal";
	import { words } from "../data/words";
	import Letre from "../compenets/Letre.svelte";
	import Gussword from "../compenets/Gussword.svelte";
    export let path;
	
	let image_src = "";
	const image_p = (x) => {
		image_src = "static/" + x + ".png";
	};

	let mot;
	let last="";
	let failCount = 0;
	let won = false;
	const word = () => {
		return words[Math.floor(Math.random() * words.length)];
	};

	const ok = (x) => {
		if(failCount < 7 && !won){
			countDownDate = new Date().getTime() + 60000;
			last = x
		}else{
			seconds = false
		}
	};

	$: image_p(failCount)
	onMount(() => {
		mot = word();
	});

	$: console.log(failCount)

	const alph = [
		"A",
		"B",
		"C",
		"D",
		"E",
		"F",
		"G",
		"H",
		"I",
		"J",
		"K",
		"L",
		"M",
		"N",
		"O",
		"P",
		"Q",
		"R",
		"S",
		"T",
		"U",
		"V",
		"W",
		"X",
		"Y",
		"Z",
	];

	/////////timer fonction start
	// Set the date we're counting down to
	let countDownDate = new Date().getTime() + 60000;
	let seconds = 60;

	// Update the count down every 1 second
	let x = setInterval(function () {
		// Get today's date and time
		let now = new Date().getTime();

		// Find the distance between now and the count down date
		let distance = countDownDate - now;

		seconds = (distance / 1000).toFixed(0)

		// If the count down is over, write some text
		if (distance < 0 || failCount >= 7) {
			clearInterval(x);
			seconds = false
		}
	}, 1000);

	///////timer fonction end

    
</script>
<div class="bg">
	<div class="home" on:click={() => {path= "home"}}>Home</div>
    <div class="refresh" on:click={() => {path= ""}}>Restart</div>
	<div class="titre">
		<h1 style="font-size:50px;color:rgb(60, 204, 168);">HANGMAN</h1>
	</div>
	<div class="word">
		<Gussword mot={mot}  bind:last={last} bind:failCount={failCount} bind:won={won} bind:seconds={seconds}/>
	</div>
	<div class="box-container">
		<div class="box-left">
			<img src={image_src} alt="Pendu " width="480px" height="480px" />
		</div>
		<div class="box-right">
			{#each alph as l}
				<Letre mot={mot} onclick={() => ok(l)} bind:l={l}/>
			{/each}
		</div>
	</div>
	<div class="time">
		<p id="timer">
			{#if seconds == false}
				Game Over
				{:else if won}
				You Won
				{:else}
				{seconds + "s "}
			{/if}
		</p>
	</div>
	<!-- <div class="square" on:click={square_click} style="background-color: {bg_color};">
		
	</div>
	 -->
</div>

<style>
	.bg {
		width: 100%;
		height: 100%;
		background-color: black;
		display: flex;
		flex-direction: column;
		position: relative;
	}
	.titre {
		display: flex;
		justify-content: center;
		align-items: center;
		margin-top: 15px;
	}

	.word {
		flex: 1;
		max-height: 80px;
		background-color: rgb(89, 165, 189);
		display: flex;
		justify-content: center;
		align-items: flex-start;
		padding: 20px;
		margin: 15px 20px 15px 20px;
		border-radius: 25px;
	}
	.box-container {
		margin: 0 20px 15px 20px;
		display: flex;
		flex-direction: row;
		flex: 1;
		max-height: 500px;
	}
	.box-left {
		flex: 1;
		background-color: rgb(220, 235, 165);
		margin-right: 7.5px;
		border-radius: 25px;
		min-width: 932.5px;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.refresh {
		position: absolute;
		right: 20px;
		top: 20px;
		color: white;
		font-size: 20px;
		cursor: pointer;
	}
    .home {
		position: absolute;
		left: 20px;
		top: 20px;
		color: white;
		font-size: 20px;
		cursor: pointer;
	}

	.box-right {
		flex: 1;
		background-color: rgb(131, 194, 185);
		max-width: 932.5px;
		margin-left: 7.5px;
		border-radius: 25px;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		flex-wrap: wrap;
		padding-left: 160px;
		padding-right: 160px;
		padding-top: 80px;
		padding-bottom: 80px;
	}

	.time {
		flex: 1;
		max-height: 80px;
		background-color: rgb(60, 204, 168);
		display: flex;
		justify-content: center;
		padding: 20px;
		margin: 0px 20px 15px 20px;
		border-radius: 25px;
	}

	#timer {
		font-size: 3em;
		margin: 0;
		margin-top: 1%;
	}
</style>
