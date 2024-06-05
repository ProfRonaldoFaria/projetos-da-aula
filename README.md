# projetos-da-aula
// ball variables
let xball = 300;
let yball = 200;
let diameter = 20;
let xballspeed = 5;
let yballspeed = 5;
let ray = diameter / 2;

// racket variables - player 1
let xrect1 = 5;
let yreact1 = 150;
let wreact1 = 10;
let hreact1 = 100;

// racket variables - player 2 machine
let xrect2 = 585;
let yreact2 = 150;
let wreact2 = 10;
let hreact2 = 100;
let speedyracket2;

//game score
let player1 = 0;
let player2 = 0;

// screen size
function setup() {
  createCanvas(600, 400);
}

// game play
function draw() {
  background(85,107,75);
  fieldlines ();
  showball ();
  moveball ();
  outskirts ();
  showracket1 (xrect1,yreact1);
  showracket2 (xrect2,yreact2);  
  moverackety1 ();
  crashracket1 ();
  moverackety2 ();
  crashracket2 ();
  score ();
}

// function parts in to the game
function fieldlines (){
  noStroke();
  rect (297.5,0,5,400);
  circle (300,200,15)
}
function showball (){
  circle (xball,yball,diameter); 
}
function moveball (){
  xball += xballspeed;
  yball -= yballspeed;
}
function outskirts (){
    if (xball + ray > width || xball - ray < 0){
    xballspeed *= - 1;
  }
    if (yball + ray > height || yball - ray < 0){
    yballspeed *= - 1;
  }
}
function showracket1 (x,y){
  rect (x,y,wreact1,hreact1);
}
function showracket2 (x,y){
  rect (x,y,wreact2,hreact2);
}
function moverackety1 (){
    if (keyIsDown(UP_ARROW)){
    yreact1 -=10;
    }
    if (keyIsDown(DOWN_ARROW)){
    yreact1 +=10;
  }
}
function crashracket1 (){
  if (xball - ray < xrect1 + wreact1 && yball - ray < yreact1 + hreact1 && yball + ray > yreact1){
   xballspeed *= - 1;
  }
}
function moverackety2 (){
  speedyracket2 = yball - yreact2 - hreact2 / 2;
  yreact2 += speedyracket2;
}
function crashracket2 (){
  if (xball + ray > xrect2 && yball - ray < yreact2 + hreact2 && yball + ray > yreact2){
   xballspeed *= - 1;
  }
}
function score (){
  textAlign (CENTER);
  textSize (25);
  fill (255);
  text (player1,270,26);
  text (player2,328,26);
  if (xball > 590){
    player1 +=1;
  }
    if (xball < 10){
    player2 +=1;
  }
}
