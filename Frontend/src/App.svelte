<script lang="ts">
  import { onMount } from 'svelte';
 import { Styles } from "sveltestrap";
 import {Row,Container,Col, FormGroup , Label, Input} from "sveltestrap/src"

  let displayTime ="01:51";
let chars = [
  ["E", "S", " ", "I", "S", "C", "H", " ", "S", "S"],
  ["Z", "W", "O", "I", "A", "C", "H", "T", "I", "E"],
  ["D", "R", "E", "I", "N", "E", "U", "N", "E", "C"],
  ["V", "I", "E", "R", "F", "Ü", "N", "F", "B", "H"],
  ["O", "I", "S", " ", "Z", "E", "H", "N", "A", "S"],
  [" ", "V", "O", "R", " ", "N", "A", "C", "H", " "],
  ["D", "R", "E", "I", "V", "I", "E", "R", "T", "L"],
  [" ", " ", " ", "H", "A", "L", "B", " ", " ", " "],
  ["O", "I", "S", " ", "S", "I", "E", "B", "N", "E"],
  ["Z", "W", "O", "I", "Z", "W", "Ö", "L", "F", "E"],
  ["D", "R", "E", "I", " ", "A", "C", "H", "T", "E"],
  ["V", "I", "E", "R", "E", "N", "E", "U", "N", "E"],
  ["F", "Ü", "N", "F", "E", "Z", "E", "H", "N", "E"],
  ["S", "E", "C", "H", "S", "E", "E", "L", "F", "E"],
];

//let isChars = Array(14).fill(Array(10).fill(false))
let isChars =[
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  [false,false,false,false,false,false,false,false,false,false,],
  ]


  function reset(){
  for(let i = 0; i < isChars.length; i++){
    for(let k = 0; k < isChars[0].length; k++){
        isChars[i][k] = false;
    }
  }
}

function setHours(num:number){

  let row = 0;
  let cols = [];
  switch(num){
    case 1:   row=8;  cols = [0,1,2];       break;
    case 2:   row=9;  cols = [0,1,2,3];     break;
    case 3:   row=10; cols = [0,1,2,3];     break;
    case 4:   row=11; cols = [0,1,2,3,4];   break;
    case 5:   row=12; cols = [0,1,2,3,4];   break;
    case 6:   row=13; cols = [0,1,2,3,4,5]; break;
    case 7:   row=8;  cols = [4,5,6,7,8,9]; break;
    case 8:   row=10; cols = [5,6,7,8,9];   break;
    case 9:   row=11; cols = [5,6,7,8,9];   break;
    case 10:  row=12; cols = [5,6,7,8,9];   break;
    case 11:  row=13; cols = [6,7,8,9];     break;
    case 12:  row=9;  cols = [4,5,6,7,8,9]; break;
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
    case 1: row=6; cols = [4,5,6,7,8,9]; break;
    case 2: row=7; cols = [3,4,5,6]; break;
    case 3: row=6; cols = [0,1,2,3,4,5,6,7,8,9]; break;
  }
  for(let i in cols){
    isChars[row][cols[i]] = true;
  }
  isChars = isChars
}

function setMinutesText(num:number){
  let row = 0;
  let cols = [];
  switch(num){
    case 0:   row=5;  cols = [1,2,3];     break;
    case 1:   row=5;  cols = [5,6,7,8];   break;
  }
  for(let i in cols){
    isChars[row][cols[i]] = true;
  }
  isChars = isChars
}

function setMinutes(num:number){
  let row = 0;
  let cols = [];
  switch(num){
    case 1:   row=4;  cols = [0,1,2];     break;
    case 2:   row=1;  cols = [0,1,2,3];   break;
    case 3:   row=2;  cols = [0,1,2,3];   break;
    case 4:   row=3;  cols = [0,1,2,3];   break;
    case 5:   row=3;  cols = [4,5,6,7];   break;
    //case 6:   row=13; cols = [0,1,2,3,4,5]; break;
    //case 7:   row=8;  cols = [4,5,6,7,8,9]; break;
    case 8:   row=1; cols =  [4,5,6,7];   break;
    case 9:   row=2; cols =  [4,5,6,7];   break;
    case 10:   row=4; cols =  [4,5,6,7];   break;
  }
  for(let i in cols){
    isChars[row][cols[i]] = true;
  }
  row =0;
  cols =[]
  switch(num){
    case 6: row=9; cols =[0,1,2,3,4];break;
    case 7: row=8; cols =[0,1,2,3,4];break;
  }
  for(let i in cols){
    isChars[cols[i]][row] = true;
  }
  isChars = isChars
}

function onTimeChange(){
  console.log(displayTime, typeof(displayTime))
  if(displayTime != undefined){
      let hours = +displayTime.split(":")[0]
      let minutes = +displayTime.split(":")[1]

      if(minutes !=0){
        hours +=1
      }

      
      reset()
      setText()
      setHours(hours%12)

      //minutes
      if(minutes >= 1 && minutes <=9){
        setMinutes(minutes)
        setMinutesText(1)
      }
      else  if(minutes >= 10 && minutes <=14){
        setMinutes(15-minutes)
        setMinutesText(0)
        setOuaters(1)
      }
      else if(minutes == 15){
        setOuaters(1)
      }
      else  if(minutes >= 16 && minutes <=19){
        setMinutes(minutes-15)
        setMinutesText(1)
        setOuaters(1)
      }
      else  if(minutes >= 20 && minutes <=29){
        setMinutes(30-minutes)
        setMinutesText(0)
        setOuaters(2)
      }
      else if(minutes == 30){
        setOuaters(2)
      }
      else  if(minutes >= 31 && minutes <=39){
        setMinutes(minutes-30)
        setMinutesText(1)
        setOuaters(2)
      }
      else  if(minutes >= 40 && minutes <=44){
        setMinutes(45-minutes)
        setMinutesText(0)
        setOuaters(3)
      }
      else if(minutes == 45){
        setOuaters(3)
      }
      else  if(minutes >= 46 && minutes <=49){
          setMinutes(minutes-45)
        setMinutesText(1)
        setOuaters(3)
      }
      else  if(minutes >= 50 && minutes <=59){
        setMinutes(60-minutes)
        setMinutesText(0)
      }
  }
}

let cntNumbers = 1;
let countOuaters = 0;
  function slideshow(){
    reset()
    setText()
    setHours(cntNumbers)
    setMinutes(cntNumbers)
    setOuaters(countOuaters)
    setMinutesText(countOuaters)

    countOuaters++;
    if(countOuaters == 4){
      countOuaters =0;
      cntNumbers++;
      if (cntNumbers >12){
        cntNumbers =1;
      }
    }
  }


  function setText(){
    let index = [0,1,3,4,5,6];
    for(let i in index){
      isChars[0][index[i]] = true;
    }  
  }
    onMount(async () => {
      onTimeChange()

      //setInterval(slideshow,200)
      isChars = isChars;
      chars = chars
	});







</script>
<Styles />
<Container>
  <Row>
    <Col>
  {#each chars as row,i}
  <Row style="heigt; 50px">

    {#each row as col,k }
    <div class="d-flex align-items-center justify-content-center outer">
      <h3 class={isChars[i][k]?" active":" "}>
        <!--{col.replace(" ", "K")}-->
        {col}
      </h3>
    </div>
    {/each}
  </Row>
  {/each}
</Col>
<Col sm=2>
  {displayTime}
  <FormGroup>
    <Label for="exampleTime">Time</Label>
    <Input
      type="time"
      name="time"
      id="exampleTime"
      placeholder="time placeholder"
      bind:value={displayTime}
      on:change={onTimeChange}
    />
  </FormGroup>
</Col>
  </Row>
</Container>


<style>
  .outer{
    width: 50px;
    height: 50px;
    background-color: black;
    /*border: 1px solid white;*/
    font-size: large;
    font-weight:1000;
    
  }
  .active{
    color: blue;
  }
 
</style>