---
layout: post
title:  "Mur Escapes!"
date:   2015-03-17
categories: interactive
---

<style>
*
{
  padding: 0px;
  margin: 0px;
}
#game
{
border: 1px solid purple;
width: 400px;
height: auto;
margin: 0 auto;
text-align: center;
background: -moz-linear-gradient(top, pink, purple);
background: -webkit-linear-gradient(top, pink, purple);
background: linear-gradient(top, pink, purple);
}
#stage
{
margin: 0 auto;
position: relative; 
width: 384px;
height: 384px;
background-color: black; 
}
.cell
{
display: block; 
position: absolute; 
width: 64px;
height: 64px;
}
p
{
width: 400px;
}
.content h1
{
font-family: impact;
color: violet;
font-size: 20px;
-webkit-text-stroke: .5px #000;
-moz-text-stroke: .5px #000;
text-stroke: .5px #000;
text-shadow: 2px 3px 2px rgba(100, 100, 0, 0.5);
letter-spacing: 10px;
}
</style>
<section id="game"></div>
<h1>mur escapes!</h1>
<div id="stage"></div>
<p id="output"></p>
</section>
<script>
//Get a reference to the stage and output
var stage = document.querySelector("#stage");
var output = document.querySelector("#output");
//Add a keyboard listener
window.addEventListener("keydown", keydownHandler, false);
//The game map
var map =
[
 	[3, 0, 2, 0, 0, 1],
	[0, 0, 0, 0, 0, 0],
	[0, 1, 0, 0, 0, 0],
	[0, 0, 0, 0, 0, 2],
	[0, 2, 0, 1, 0, 0],
	[0, 0, 0, 0, 0, 0]
];
//The game objects map
var gameObjects =
[
  [0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0],
  [0, 0, 0, 5, 0, 0],
  [0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 0],
  [0, 0, 0, 0, 0, 4]
];
//Map code
var WATER = 0;
var FOOD = 1;
var CHUBCHUB = 2;
var BED = 3;
var mur = 4;
var HAND= 5;
//Stats Variables
var calories= 100;
var effort= 0;
var acceleration= 1;
var mass= 100;
var force= 100;

var SIZE = 64;
//The number of rows and columns
var ROWS = map.length;
var COLUMNS = map[0].length;
//Arrow key codes
var UP = 38;
var DOWN = 40;
var RIGHT = 39;
var LEFT = 37;

var murRow;
var murColumn;
var handRow;
var handColumn;
for(var row = 0; row < ROWS; row++) 
{	
  for(var column = 0; column < COLUMNS; column++) 
  {
    if(gameObjects[row][column] === mur)
    { 
      murRow = row;
      murColumn = column;
    }
	if(gameObjects[row][column] === HAND)
    { 
      handRow = row;
      handColumn = column;
    }
  }
}
render();
function keydownHandler(event)
{
  switch(event.keyCode)
  {
    case UP:
      
      //Find out if the mur's move will
      //be within the playing field
	    if(murRow > 0)
	    {
	      //If it is, clear the mur's current cell
	      gameObjects[murRow][murColumn] = 0;
	      
	      //Subract 1 from the mur's row
	      //to move it up one row on the map
	      murRow--;
		
	      
	      //Apply the mur's new updated position to the array
	      gameObjects[murRow][murColumn] = mur;
		  acceleration++;
	    }
	    break;
	  
	  case DOWN:
	    if(murRow < ROWS - 1)
	    {
	      gameObjects[murRow][murColumn] = 0;
	      murRow++;
	      gameObjects[murRow][murColumn] = mur;
	    }
	    break;
	    
	  case LEFT:
	    if(murColumn > 0)
	    {
	      gameObjects[murRow][murColumn] = 0;
	      murColumn--;
	      gameObjects[murRow][murColumn] = mur;
	    }
	    break;  
	    
	  case RIGHT:
	    if(murColumn < COLUMNS - 1)
	    {
	      gameObjects[murRow][murColumn] = 0;
	      murColumn++;
	      gameObjects[murRow][murColumn] = mur;
	    }
	    break; 
  }
  
  switch(map[murRow][murColumn])
  {
	case WATER:
	if(mass <=100)
{
gameMessage="Find some food or accelerate at ChubChub.";
}
else
{
gameMessage="Get to the bed!";
}
	
	break;
	
	case CHUBCHUB:
	fight();
	break;
	
	case FOOD:
	eat();
	break;
	
	case BED:
	endGame();
	break;
}
  moveHand();
  
 if(gameObjects[murRow][murColumn] === HAND)
{
endGame();
}  
  
//Subtract some energy each turn
acceleration-= .25;
effort+= 15;
calories--;
mass= calories- effort;
force= Math.round(mass * acceleration);
if(force <= 0 || acceleration <=0 || mass <=0)
{
endGame();
}
  
  //Render the game
  render();
}
function render()
{
  //Clear the stage of img cells
  //from the previous turn
  
  if(stage.hasChildNodes())
  {
    for(var i = 0; i < ROWS * COLUMNS; i++) 
    {	 
      stage.removeChild(stage.firstChild);
    }
  }
  
  //Render the game by looping through the map arrays
  for(var row = 0; row < ROWS; row++) 
  {	
    for(var column = 0; column < COLUMNS; column++) 
    { 
      //Create a img tag called cell
      var cell = document.createElement("img");
      //Set it's CSS class to "cell"
      cell.setAttribute("class", "cell");
      //Add the img tag to the <div id="stage"> tag
      stage.appendChild(cell);
      //Find the correct image for this map cell
      switch(map[row][column])
      {
        case WATER:
          cell.src = "/img/floor.png";
          break;
        case FOOD:
          cell.src = "/img/catfood.png";
          break; 
        case CHUBCHUB:
          cell.src = "/img/chubchub2.gif";
          break; 
        case BED:
          cell.src = "/img/bed.png";
          break;   
      }  
      
      //Add the mur from the gameObjects array
	    switch(gameObjects[row][column])
	    {
	    case mur:
	        cell.src = "/img/MUR2.gif";
	        break;
		
		case HAND: 
			cell.src= "/img/HAND2.gif";
			break;
			
	    } 
  
      //Position the cell 
      cell.style.top = row * SIZE + "px";
      cell.style.left = column * SIZE + "px";
    }
  }
  
  output.innerHTML= gameMessage + "<br><b>calories:</b> " + calories + "<br><b>effort:</b> " + effort + "<br><b>force:</b> " + force
  + "<br><b>acceleration:</b> " + acceleration + "<br><b>mass:</b> " + mass;
  
}
function eat()
{
var catfood= Math.round((effort/murRow) * murColumn) + 2;
calories += catfood;
gameMessage= "You ate " + catfood + " calories of food!";
//var mass= calories- effort; 
//var force= mass * acceleration;
//when successfully eating, add to effort and double acceleration
//when unsuccessfully eating, add to effort and subtract from acceleration
//var food= Math.round(Math.random() * 10);
//console.log(food);
}
function fight()
{
var chubchubForce= Math.ceil(Math.random() * force * 2);
if(chubchubForce > force)
{
acceleration -= Math.round(chubchubForce / 10);
gameMessage= "ChubChub growls and you turn around. ChubChub's force: "
+ chubchubForce;
}
else 
{
calories+= chubchubForce;
acceleration += Math.round(chubchubForce / 10);
gameMessage= "You scratched ChubChub and won " + chubchubForce + " calories of food.";
}
effort += Math.round(chubchubForce / 4);
}
function moveHand()
{
var UP= 1;
var DOWN= 2;
var LEFT= 3;
var RIGHT= 4;
var validDirections= [];
var direction= undefined;
if(handRow > 0)
{
var thingAbove = map[handRow- 1][handColumn];
if(thingAbove === WATER)
{
validDirections.push(UP)
}
}
if(handRow < ROWS -1)
{
var thingBelow= map[handRow +1][handColumn];
if(thingBelow === WATER)
{
validDirections.push(DOWN)
}
}
if(handColumn > 0)
{
var thingToTheLeft= map[handRow][handColumn -1];
if(thingToTheLeft === WATER)
{
validDirections.push(LEFT)
}
}
if(handColumn < COLUMNS - 1)
{
var thingToTheRight = map[handRow][handColumn + 1];
if(thingToTheRight=== WATER)
{
validDirections.push(RIGHT)
}
}
if(validDirections.length !==0)
{
var randomNumber= Math.floor(Math.random() * validDirections.length);
direction= validDirections[randomNumber];
}
switch(direction)
{
case UP: 
gameObjects[handRow][handColumn] = 0;
handRow--;
gameObjects[handRow][handColumn] = HAND;
break;
case DOWN:
gameObjects[handRow][handColumn] = 0;
handRow++;
gameObjects[handRow][handColumn] = HAND;
break;
case LEFT:
gameObjects[handRow][handColumn] = 0;
handColumn--;
gameObjects[handRow][handColumn] = HAND;
break;
case RIGHT:
gameObjects[handRow][handColumn] = 0;
handColumn++;
gameObjects[handRow][handColumn] = HAND;
break;
}
}
function endGame()
{
if(map[murRow][murColumn]=== BED)
{
var score= Math.round(force + effort);
	
	gameMessage= "You made it to the bed! " + " Final Score: " + score;
}
else if(gameObjects[murRow][murColumn] === HAND)
{
gameMessage += "<br>The hand caught you!";
}
else if(acceleration <= 0)
{
gameMessage += "<br>You cannot accelerate!";
gameMessage += " The dogs surround you!";
}
else
{
gameMessage += "<br>You ran out of strength!";
gameMessage += " The dogs surround you!";
}
window.removeEventListener("keydown", keydownHandler, false);
}
</script>
