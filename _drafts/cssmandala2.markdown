---
layout: post
title:  "Mandala #2"
date:   2015-03-17
categories: interactive
---
<style>
.mandala{
  position: relative;
  top: 50px;
  margin: auto;
  width: 500px;
  height: 500px;
  background-color: #dddddd;
  border-radius: 50%;
  overflow: hidden;
    -webkit-perspective: 800px;
  -moz-perspective: 800px;
  -o-perspective: 800px;
  perspective: 800px;
}
.wheel{
  position: absolute;
  width: 500px;
  height: 500px;
  background-color: black;
  border-radius: 50%;
  overflow: hidden;
  -webkit-user-select: none;
  -moz-user-select: none;
  user-select: none;
}

.innercircle{
  left: 25%;
  height: 50%;
  position: absolute;
  width: 50%;
  top: 0px;
  background-color: LightBlue;
  transform-origin: bottom center;
  text-align: center;
  cursor: pointer;
}

.innercircle:hover{
     background-color: black;
  color: white;
}

.c1 { transform: rotate(72deg); 
background-color: red;}
.c2 { transform: rotate(144deg);
background-color: yellow;}
.c3 { transform: rotate(216deg);
background-color: green;}
.c4 { transform: rotate(288deg); 
background-color: blue;
  cursor: -webkit-grab;
 color: white;
  font-size: 2em;
}
.c4:hover{
  background-color: blue;
}

.c4 h1{
  position: absolute;
  top: -50px;
  left: 1.5em;
}
.c5 { transform: rotate(360deg);
background-color: purple;}

.cap{
left: 10%;
  height: 400px;
  position: relative;
  width: 400px;
  top: 10%;
  background-color: black;
  border-radius: 50%;
  
  -webkit-perspective: 600px;
  -moz-perspective: 600px;
  -o-perspective: 600px;
  perspective: 600px;

  
}



.card{

  height: 400px;
  position: absolute;
  width: 400px;
  background-color: LightBlue;
  border-radius: 50%;
  text-align: center;
   border-radius: 50%;
  -webkit-transition: -webkit-transform 0.4s;
  -moz-transition: -moz-transform 0.4s;
  -o-transition: -o-transform 0.4s;
  transition: transform 0.4s;
  -webkit-transform-style: preserve-3d;
  -moz-transform-style: preserve-3d;
  -o-transform-style: preserve-3d;
  transform-style: preserve-3d;
  z-index: 10;

}

.card .front,
.card .back{
  overflow: hidden;
  display: block;
  position: absolute;
    height: 100%;
  width: 100%;
   border-radius: 50%;
  -webkit-backface-visibility: hidden;
  -moz-backface-visibility: hidden;
  -o-backface-visibility: hidden;
  backface-visibility: hidden;
   z-index: 11;
}
.card .back{
  position: absolute;
  border: 1px solid;
    -webkit-transform: rotateY( 180deg );
  -moz-transform: rotateY( 180deg );
  -o-transform: rotateY( 180deg );
  transform: rotateY( 180deg );
 
}


.card.flipped{
   -webkit-transform: rotateY( 180deg );
  -moz-transform: rotateY( 180deg );
  -o-transform: rotateY( 180deg );
  transform: rotateY( 180deg );
}


.selected{
  background-color: black;
  color: white;
}

.card section{
  position: absolute;
  width: 100%;
  height: 100%;
  border: 2px solid black;
  border-radius: 50%;
}

.card section p{
  position: absolute;
margin: 20% 10% 10% 10%;
  text-align: center;
}
</style>


<div class="mandala">
  <div class="wheel">
    <div class="innercircle c1"><h1>about</h1></div>
  <div class="innercircle c2"><h1>clients</h1></div>
  <div class="innercircle c3"><h1>contact</h1></div>
 <div class="innercircle c4"><h1>&#10162;</h1></div>
 <div class="innercircle c5"><h1>home</h1></div>
<div class="cap">
  <div class="card">
  <div class="face front"><section>
    Front</section>
            </div> 
            <div class="face back"><section><p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nemo perferendis architecto qui, numquam ea earum ab ducimus blanditiis fugiat, veniam cum, hic facilis atque dolorum laboriosam? Repellendus, facilis. Molestias, officiis!</p></section>
            </div> 
</div>
    </div>
    </div>
</div>

<script>
var rotation = 0;
var card= $('.card');
var txt= $('.card section')
jQuery.fn.rotate = function(degrees) {
    $(this).css({'-webkit-transform' : 'rotate('+ degrees +'deg)',
                 '-moz-transform' : 'rotate('+ degrees +'deg)',
                 '-ms-transform' : 'rotate('+ degrees +'deg)',
                 'transform' : 'rotate('+ degrees +'deg)'});
};

$('.wheel').draggable({ containment: 'parent', handle: '.c4', drag: function() {
    rotation += 10;
    $(this).rotate(rotation);
     $(txt).rotate(rotation * -1);
}});

var tab= $('.innercircle');
$(tab).click(function(){
    for(i=0; i< tab.length; i++){
    $(tab).removeClass('selected');
  }
  $(this).addClass('selected');

});


$(card).click(function(){

  $(this).toggleClass('flipped');
  
});
</script>