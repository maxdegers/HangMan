<script>
    export let onclick;
    export let mot = "";
    export let l = "";

    let color = ""
    let clicked = false
    const myClick = () => {
        onclick()
        
        if(mot.includes(l.toLowerCase())){
            color = "green"
        }
        else{
            color = "red"
        }
        
        clicked = true

    }
</script>

<!-- on:mouseover={"background-color: rgb(197, 202, 152)"} on:mouseout={"background-color: rgb(224, 230, 174)"} -->
<div class="Letre" style="{clicked? "background-color:"+color: ""}" on:click={myClick} >
    {l}
</div>
<style>

.Letre{
    display: flex;
    justify-content: center;
	align-items: center;
    font-size:50px;
    width: 50px;
    height: 50px;
    border-radius: 10px;
    padding: 5px;
	margin: 10px 5px 5px 5px;
    background-color: rgb(224, 230, 174);
    
    border: 1px solid #000;
    
}

.Letre:hover {
    background-color: rgb(189, 194, 149);
    cursor: pointer;
}

</style>
