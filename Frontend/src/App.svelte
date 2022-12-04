<script lang="ts">
  import { onMount } from 'svelte';
 import { Styles } from "sveltestrap";
 import {Row,Container} from "sveltestrap/src"

let chars = [
  [ "E","S"," ","I","S","C","H"," ","H","A","L","B"],
  [ " "," ","D","R","E","I","V","I","E","R","T","L"],
  [ "O","I","S","Z","W","O","I","D","R","E","I"," "],
  [ "V","I","E","R","E","F","Ü","N","F","E"," "," "],
  [ "S","E","C","H","S","E","S","I","E","B","N","E"],
  [ "A","C","H","D","E","N","E","I","N","E"," "," "],
  [ "E","L","F","E","Z","W","E","L","F","E"," "," "],
];

let isChars = [
  Array(12).fill(false),
  Array(12).fill(false),
  Array(12).fill(false),
  Array(12).fill(false),
  Array(12).fill(true),
  Array(12).fill(false),
  Array(12).fill(false),
  
  ];

function reset(){
  for(let i = 0; i < isChars.length; i++){
    for(let k = 0; k < isChars[0].length; k++){
    isChars[i][k] = false;
  }
  }
}

  function setText(){
    let index = [0,1,3,4,5,6];
    for(let i in index){
      isChars[0][index[i]] = true;
    }  }
    onMount(async () => {
 
      console.log("sfd");
		  setText();

      isChars = isChars;
      chars = chars
      console.log("ssadf");
	});







</script>
<Styles />

  <button on:click={reset}>reset</button>
  <button on:click={setText}>test</button>
<Container>
  {#each chars as row,i}
  <Row style="heigt; 50px">

    {#each row as col,k }
    <div class="d-flex align-items-center justify-content-center outer">
      <h1 class={isChars[i][k]?" active":" "}>
        {col.replace(" ", "K")}
      </h1>
    </div>
    {/each}
  </Row>
  {/each}
</Container>


<style>
  .outer{
    width: 75px;
    height: 75px;
    background-color: black;
    /*border: 1px solid white;*/
    font-size: large;
    font-weight:1000;
    
  }
  .active{
    color: blue;
  }
 
</style>