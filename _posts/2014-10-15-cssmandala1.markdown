---
layout: post
title:  "CSS Mandala #1"
date:   2014-10-15
categories: graphic
tags: mandala, css
---
<style>

.mandala{
  position: relative;
  margin: auto;
  width: 300px;
  height: 300px;
  background-color: #dddddd;
  -webkit-border-radius: 300px;
  -moz-border-radius: 300px;
  border-radius: 300px;
  overflow: hidden;
}

.heavens{
  position: absolute;
  height: 20%;
  width: 100%;
  background-color: DarkBlue;
  -webkit-animation: nightandday 24s ease-in infinite;
  -moz-animation: nightandday 24s ease-in infinite;
  animation: nightandday 24s ease-in infinite;
}
.sky{
  position: absolute;
  top: 20%;
  height: 20%;
  width: 100%;
  background-color: LightBlue;
  -webkit-animation: 24s getdark linear 0s infinite;
  -moz-animation: 24s getdark linear 0s infinite;
  animation: 24s getdark linear 0s infinite;
}
.earth{
  position: absolute;
  top: 40%;
  height: 10%;
  width: 100%;
  background-color: DarkOliveGreen;
  z-index: 1;
}
.sea{
  position: absolute;
  top: 50%;
  height: 20%;
  width: 100%;
  background-color: SeaGreen;
  z-index: 2;
}

.sea:after {
content: " ";
    display:block;
    position: relative;
top:0;left:0;
    width:100%;
    height:20px;
    background: linear-gradient(transparent 0, transparent 0), linear-gradient(135deg, SeaGreen 50.33%, transparent 33.33%) 0 0, linear-gradient(45deg, SeaGreen 50.33%, SeaGreen 33.33%) 0 0;
  
    background: -webkit-linear-gradient(transparent 0, transparent 0), -webkit-linear-gradient(135deg, SeaGreen 50%, transparent 33.33%) 0 0, SeaGreen -webkit-linear-gradient(45deg, SeaGreen 50%, DarkOliveGreen 33.33%) 0 0;
    background: -webkit-gradient(transparent 0, transparent 0), -webkit-gradient(135deg, SeaGreen 50%, transparent 33.33%) 0 0, SeaGreen -webkit-gradient(45deg, SeaGreen 50%, DarkOliveGreen 33.33%) 0 0;
    background: -o-linear-gradient(transparent 0, transparent 0), -o-linear-gradient(135deg, SeaGreen 33.33%, transparent 33.33%) 0 0, SeaGreen -o-linear-gradient(45deg, #272220 33.33%, #2B3A48 33.33%) 0 0;
    background: -moz-linear-gradient(transparent 50%, transparent 0), -moz-linear-gradient(135deg, SeaGreen 33.33%, transparent 33.33%) 0 0, SeaGreen -moz-linear-gradient(45deg, SeaGreen 33.33%, SeaGreen 33.33%) 0 0;
    background-repeat: repeat-x;
    background-size: 5px 150%, 20px 27px, 9px 27px;
  width: 500%;
  margin-left: -50%;
  -webkit-animation: movesea 10s
    infinite alternate;
   -moz-animation: movesea 10s
    infinite alternate;
  animation: movesea 10s
    infinite alternate;
 
    }
.stone{
  position: absolute;
  top: 70%;
  height: 10%;
  width: 100%;
  background-color: SlateGray;
}
.underworld{
  position: absolute;
  top: 80%;
  height: 20%;
  width: 100%;
  background-color: FireBrick;
}

/*objects*/


/*sun*/
 .sun{
 position: absolute;
  background-color: yellow;
  width: 25px;
  height: 25px;
  -webkit-border-radius: 25px;
   border-radius: 25px;
   z-index: 1;
   top: 0;
   left: 0;
   -webkit-animation: movesun 24s infinite;
   -moz-animation: movesun 24s infinite;
   animation: movesun 24s infinite;
 }

/*Stars*/
.star{
 position: absolute;
  background-color: white;
  width: 3px;
  height: 6px;
  -webkit-border-radius: 10px;
-moz-border-radius: 10px;
   border-radius: 10px;
}

/*Big Dipper*/
.bigdipper{
  position: absolute;
  
  top: -10px;
  left: -120px;
  -webkit-animation: starcurtain 24s linear 18s infinite;
  -moz-animation: starcurtain 24s linear 18s infinite;
  animation: starcurtain 24s linear 18s infinite;
}

.s1{
    left: 150px;
  top: 50px;
}
.s2{
     left: 170px;
  top: 40px;
}
.s3{
     left: 200px;
  top: 40px;
}
.s4{
     left: 230px;
  top: 50px;
}
.s5{
     left: 280px;
  top: 45px;
}
.s6{
     left: 240px;
  top: 75px;
}
.s7{
     left: 275px;
  top: 80px;
}
/*cloud*/
.cloud{
  position: absolute;
  background-color: transparent;
  width: 100px;
  height: 50px;
  left: 50px;
  top: 20px;
  -webkit-animation: wind 20s linear 0s infinite;
  -moz-animation: wind 20s linear 0s infinite;
  animation: wind 20s linear 0s infinite;
  z-index: 9;
}

.cloud_left{
  position: absolute;
  background-color: white;
  width: 40px;
  height: 25px;
  -webkit-border-radius: 40px 10px 40px 0;
  -moz-border-radius: 40px 10px 40px 0;
  border-radius: 40px 10px 40px 0;
-webkit-box-shadow: 0 1px 5px gray;
  -moz-box-shadow: 0 1px 5px gray;
  box-shadow: 0 1px 5px gray;
  z-index: 5;
}

.cloud_middle{
   position: absolute;
  background-color: white;
  width: 40px;
  height: 40px;
  -webkit-border-radius: 50px 50px 0 0;
  -moz-border-radius: 50px 50px 0 0;
  border-radius: 50px 50px 0 0;
   -webkit-box-shadow: 1px 0 5px gray;
  -moz-box-shadow: 1px 0 5px gray;
  box-shadow: 1px 0 5px gray;
  left: 25px;
  top: -15px;
  
    z-index: 4;
}

.cloud_right{
  position: absolute;
  background-color: white;
  width: 40px;
  height: 25px;
  -webkit-border-radius: 10px 40px 0 0;
  -moz-border-radius: 10px 40px 0 0;
  border-radius: 10px 40px 0 0;
  -webkit-box-shadow: 1px 0 5px gray;
  -moz-box-shadow: 1px 0 5px gray;
  box-shadow: 1px 0 5px gray;
  left: 50px;
    z-index: 5;

  

}

.c1{
  left: 200px;
  -webkit-animation: wind 30s infinite;
  -moz-animation: wind 30s infinite;
  animation: wind 30s infinite;
  z-index: 10;
}
.c2{
  left: 350px;
  -webkit-animation: wind 40s linear infinite alternate;
  -moz-animation: wind 40s linear infinite alternate;
  animation: wind 40s linear infinite alternate;
  z-index: 12;
}
.c3{
  left: 350px;
  -webkit-animation: wind 19s infinite alternate;
  -moz-animation: wind 19s infinite alternate;
  animation: wind 19s infinite alternate;
  z-index: 11;
}

/*the whale*/
.whale{
position: absolute;
background-color: transparent;
  width: 100px;
  height: 30px;
  top: 50px;
  left: 500px;
  -webkit-animation: swim 20s linear 10s infinite;
  -moz-animation: swim 20s linear 10s infinite;
  animation: swim 20s linear 10s infinite;
}

.whale_body{
    position: absolute;
  width: 80px;
  height: 30px;
  background-color: #99CCFF;
  -webkit-border-radius: 50px 20px 50px 20px;
  -moz-border-radius: 50px 20px 50px 20px;
  border-radius: 50px 20px 50px 20px;

}

.whale_tail{
     position: absolute;
  width: 20px;
  height: 10px;
   background-color: #99CCFF;
  left: 70px;
  -webkit-transform: skewy(50deg);
  -moz-transform: skewy(50deg);
  -ms-transform: skewy(50deg);
  -o-transform: skewy(50deg);
  transform: skewy(50deg);
  -webkit-box-shadow: 2px 2px black;
  -moz-box-shadow: 2px 2px black;
  box-shadow: 2px 2px black;
   -webkit-animation: movetail 2s infinite;
  -moz-animation: movetail 2s infinite;
  animation: movetail 2s infinite;
  
}

.whale_head{
    position: absolute;
  width: 30px;
  height: 28px;
  background-color: #99CCFF;
  -webkit-border-radius: 50px 20px 50px 20px;
  border-radius: 50px 20px 50px 20px;
  -webkit-box-shadow: 0 5px black;
  -moz-box-shadow: 0 5px black;
  box-shadow: 0 5px black;
}


.whale_eye{
   position: absolute;
  width: 10px;
  height: 10px;
   background-color: white;
    -webkit-border-radius: 50px 20px 50px 20px;
  -moz-border-radius: 50px 20px 50px 20px;
  border-radius: 50px 20px 50px 20px;
  left: 10px;
  top: 10px;
}

.whale_pupil{
   position: absolute;
  width: 5px;
  height: 5px;
   background-color: black;
    -webkit-border-radius: 20px;
  -moz-border-radius: 20px;
  border-radius: 20px;
  left: 2px;
  top: 2px;
}

/* animations */
 @-webkit-keyframes swim{
   from{left: 550px;}
   
   to{left: -150px;}
 }
@keyframes swim{
   from{left: 550px;}
   
   to{left: -150px;}
 }
 @-webkit-keyframes movetail{
   from{}
   
   to{top:1px;
   left: 68px;}
 }
@keyframes movetail{
   from{}
   
   to{top:1px;
   left: 68px;}
 }

 @-webkit-keyframes wind{
   from{left: -150px;}
   to{left:500px;}
 }
@keyframes wind{
   from{left: -150px;}
   to{left:500px;}
 }
 @-webkit-keyframes nightandday{
   from{background-image: radial-gradient(ellipse farthest-corner at -50% 100px , #CCFFFF 0%, rgba(100, 0, 255, 0) 50%, #CC00FF 95%);}
   50%{
     background-image: radial-gradient(ellipse farthest-corner at 50% 50% , #00FFFF 0%, rgba(0, 0, 255, 0.2) 150%, #0000FF 95%);
   }
   to{background-image: radial-gradient(ellipse farthest-corner at  150% 100px, #CCFFFF 0%, rgba(0, 0, 255, 0.2) 50%, #0000FF 95%);}
 }
@keyframes nightandday{
   from{background-image: radial-gradient(ellipse farthest-corner at -50% 100px , #CCFFFF 0%, rgba(100, 0, 255, 0) 50%, #CC00FF 95%);}
   50%{
     background-image: radial-gradient(ellipse farthest-corner at 50% 50% , #00FFFF 0%, rgba(0, 0, 255, 0.2) 150%, #0000FF 95%);
   }
   to{background-image: radial-gradient(ellipse farthest-corner at  150% 100px, #CCFFFF 0%, rgba(0, 0, 255, 0.2) 50%, #0000FF 95%);}
 }
 @-webkit-keyframes getdark{
   from{background-color: DarkBlue;}
   40%{
     background-color: LightBlue;
   }
   to{background-color: DarkBlue;}
 }
@keyframes getdark{
   from{background-color: DarkBlue;}
   40%{
     background-color: LightBlue;
   }
   to{background-color: DarkBlue;}
 }

 @-webkit-keyframes movesun{
   from{
     top: 200px;
     left: -5%;}
   50%{
     left: 50%;
     top: 50px;
   }
   to{left:105%;
   top: 200px;}
 }
@keyframes movesun{
   from{
     top: 200px;
     left: -5%;}
   50%{
     left: 50%;
     top: 50px;
   }
   to{left:105%;
   top: 200px;}
 }

 @-webkit-keyframes movesea{
   from{left: 50%;}
   to{left: -50%;}
 }
@keyframes movesea{
   from{left: 50%;}
   to{left: -50%;}
 }
 @-webkit-keyframes starcurtain{
   from{left: 50%;}
   to{left: -100%;}
 }
@keyframes starcurtain{
   from{left: 50%;}
   to{left: -100%;}
 }
</style>
<div class="wrapper">
<div class="mandala">
  <div class="heavens">
    <div class="sun"></div>
    <div class="bigdipper">
      <div class="star s1"></div>
     <div class="star s2"></div>
     <div class="star s3"></div>
    <div class="star s4"></div>
    <div class="star s5"></div>
     <div class="star s6"></div>
     <div class="star s7"></div>
      </div>
  </div>
<div class="sky">
  <div class="cloud">
    <div class="cloud_left"></div>
    <div class="cloud_middle"></div>
    <div class="cloud_right"></div>
  </div>
    <div class="cloud c1">
    <div class="cloud_left"></div>
    <div class="cloud_middle"></div>
    <div class="cloud_right"></div>
  </div>
    <div class="cloud c2">
    <div class="cloud_left"></div>
    <div class="cloud_middle"></div>
    <div class="cloud_right"></div>
  </div>
  <div class="cloud c3">
    <div class="cloud_left"></div>
    <div class="cloud_middle"></div>
    <div class="cloud_right"></div>
  </div>
</div>
<div class="earth"></div>
  <div class="sea">
    <div class="whale">
      <div class="whale_body">
        <div class="whale_head">
        <div class="whale_eye">
          <div class="whale_pupil"></div>
        </div>
         </div>
      </div>
      <div class="whale_tail"></div>
    </div>
  </div>
  <div class="stone"></div>
  <div class="underworld"></div>
</div>
</div>