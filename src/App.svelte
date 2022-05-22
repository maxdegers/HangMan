<script>
import Game from "./page/Game.svelte";
import Home from "./page/Home.svelte";
import Refresh from "./page/Refresh.svelte";
let path = "home"

</script>

{#if path == "home"}
<Home bind:path={path}/>
	{:else if path == "game"}
<Game bind:path={path}/>
	{:else if path == ""}
<Refresh bind:path={path}/>
	{/if}