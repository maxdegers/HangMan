<script>
    export let path;

</script>

<div class="bg">
    <div>
        <img src="static/logo.png" alt="">
    </div>
    <div class="bg">
         <div class="box">
        <div class="titre">
            <h1 style="font-size:50px">Rules</h1>
        </div>
        <div class="texte">
            <div class="gauche">
            <p style="font-size:25px">Game play: a random word is chosen; the player tries to guess what it is, one letter at a time. The computer draws a number of dashes equivalent to the number of letters in the word. If the player suggests a letter and gets it right, that letter will appear in the right place. If the word does not contain the suggested letter, one part of the hangman’s body will appear. As the game progresses, more and more body parts will be added for every wrong letter. The number of incorrect guesses is 7.</p>
            </div>
            <dir class="droit">
            <p style="font-size:25px">Objective: Guess the word/phrase before your man gets hung!</p>
        </dir>
        </div>
        
        
        </div>
    <div class="boton" >
        <h1 on:click={()=>{path= "game"}} style="font-size:50px;color:rgb(60, 204, 168);">Jouer</h1>
    </div>
    </div>
   


</div>



<style>
    .boton{
        display: flex;
		justify-content: center;
		align-items: center;
		margin-top: 15px;
        background-color: black;
    }
    .bg {
		width: 100%;
		height: 100%;
		background-color: black;
		display: flex;
		flex-direction: column;
		position: relative;
	}
    .box{
        flex-direction: column;
		max-height: 400px;
		background-color: rgb(197, 77, 47);
		display: flex;
		justify-content: center;
		padding: 15px;
		margin: 20px 0px 0px 20px;
		border-radius: 25px;
        max-height: 600px;
        
    }
    .texte{
        display: flex;
		justify-content: center;
		align-items: center;
		margin-top: 15px;
    }
    .gauche{
        display: flex;
        max-width: 60%;
        justify-content: center;
    }
    .droit{
        display: flex;
        max-width: 30%;
        margin: 0px 20px 0px 20px;
        justify-content: center;
    }
    .titre{
        display: flex;
		justify-content: center;
		align-items: center;
		margin: 0px ;

    }
</style>