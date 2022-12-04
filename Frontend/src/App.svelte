<script lang="ts">
  import { onMount } from 'svelte';
 import { Styles } from "sveltestrap";
 import {Row,Container} from "sveltestrap/src"

let chars = [
  [ "E","S"," ","I","S","C","H"," ","H","A","L","B"],
  [ " "," ","D","R","E","I","V","I","E","R","T","L"],
  [ "O","I","S","Z","W","O","I","D","R","E","I"," "],
  [ " ","V","I","E","R","E"," ","F","Ü","N","F","E",],
  [ "S","E","C","H","S","E","S","I","E","B","N","E"],
  [ " ","A","C","H","D","E"," ","N","E","U","N","E"],
  [ " "," ","Z","E","H","N","E"," ","E","L","F", "E"],
  [ " "," "," "," ","Z","W","Ö","L","F","E"," "," "],
];

let isChars = [
  Array(12).fill(false),
  Array(12).fill(false),
  Array(12).fill(false),
  Array(12).fill(false),
  Array(12).fill(false),
  Array(12).fill(false),
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

function setNumber(num:number){
  let row = 0;
  let cols = [];
  switch(num){
    case 1: row=2; cols = [0,1,2]; break;
    case 2: row=2; cols = [3,4,5,6]; break;
    case 3: row=2; cols = [7,8,9,10]; break;
    case 4: row=3; cols = [1,2,3,4,5]; break;
    case 5: row=3; cols = [7,8,9,10,11]; break;
    case 6: row=4; cols = [0,1,2,3,4,5]; break;
    case 7: row=4; cols = [6,7,8,9,10,11,12]; break;
    case 8: row=5; cols = [1,2,3,4,5]; break;
    case 9: row=5; cols = [7,8,9,10,11]; break;
    case 10: row=6; cols = [2,3,4,5,6]; break;
    case 11: row=6; cols = [8,9,10,11]; break;
    case 12: row=7; cols = [4,5,6,7,8,9]; break;
  }
  for(let i in cols){
    isChars[row][cols[i]] = true;
  }
  isChars = isChars
}
function setOuaters(num: number){
  let row = 0;
  let cols = [];
  switch (num) {
    case 1: row=1; cols = [6,7,8,9,10,11]; break;
    case 2: row=0; cols = [8,9,10,11]; break;
    case 3: row=1; cols = [2,3,4,5,6,7,8,9,10,11]; break;
  }
  for(let i in cols){
    isChars[row][cols[i]] = true;
  }
  isChars = isChars
}

let cntNumbers = 1;
let countOuaters = 0;
  function slideshow(){
    reset()
    setText()
    setNumber(cntNumbers)
    setOuaters(countOuaters)

    countOuaters++;
    if(countOuaters == 4){
      countOuaters =0;
      cntNumbers++;
    }
  }


  function setText(){
    let index = [0,1,3,4,5,6];
    for(let i in index){
      isChars[0][index[i]] = true;
    }  }
    onMount(async () => {
      setInterval(slideshow,2000)
      console.log("sfd");
		  setText();
      setNumber(1)

      isChars = isChars;
      chars = chars
      console.log("ssadf");
	});







</script>
<Styles />
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