[The shapes of CSS](https://css-tricks.com/examples/ShapesOfCSS/)

http://one-div.com/

http://lynnandtonic.github.io/a-single-div/

http://cssaz.tumblr.com/

http://www.bchanx.com/logos-in-pure-css-demo

#The Shapes of CSS

##Square

````
#square {
	width: 100px;
	height: 100px;
	background: red;
}
````
![1](https://cloud.githubusercontent.com/assets/5993597/7499796/e419d6a4-f3f7-11e4-8492-6d24c94b14eb.jpg)
##Rectangle
````
#rectangle {
	width: 200px;
	height: 100px;
	background: red;
}
````	
![2](https://cloud.githubusercontent.com/assets/5993597/7499797/e6b950c4-f3f7-11e4-91ba-9a4881fb77ad.jpg)
##Circle
````
#circle {
	width: 100px;
	height: 100px;
	background: red;
	-moz-border-radius: 50px;
	-webkit-border-radius: 50px;
	border-radius: 50px;
}
/* Cleaner, but slightly less support: use "50%" as value */
````	
![3](https://cloud.githubusercontent.com/assets/5993597/7499800/ed613680-f3f7-11e4-9531-ffdffc569d97.jpg)
##Oval
````
#oval {
	width: 200px;
	height: 100px;
	background: red;
	-moz-border-radius: 100px / 50px;
	-webkit-border-radius: 100px / 50px;
	border-radius: 100px / 50px;
}
/* Cleaner, but slightly less support: use "50%" as value */
````	
![4](https://cloud.githubusercontent.com/assets/5993597/7499801/eeec148e-f3f7-11e4-916d-8c2d2c8165e0.jpg)
##Triangle Up
````
#triangle-up {
	width: 0;
	height: 0;
	border-left: 50px solid transparent;
	border-right: 50px solid transparent;
	border-bottom: 100px solid red;
}
````
![5](https://cloud.githubusercontent.com/assets/5993597/7499807/fa3cd6ac-f3f7-11e4-86f9-9ed388545db7.jpg)
##Triangle Down
````
#triangle-down {
	width: 0;
	height: 0;
	border-left: 50px solid transparent;
	border-right: 50px solid transparent;
	border-top: 100px solid red;
}
````
![6](https://cloud.githubusercontent.com/assets/5993597/7499841/fcd289e8-f3f7-11e4-843f-8bd76e45c4a9.jpg)
##Triangle Left
````
#triangle-left {
	width: 0;
	height: 0;
	border-top: 50px solid transparent;
	border-right: 100px solid red;
	border-bottom: 50px solid transparent;
}
````
![7](https://cloud.githubusercontent.com/assets/5993597/7499844/fce50398-f3f7-11e4-9b65-d36628ff6e1a.jpg)
##Triangle Right
````
#triangle-right {
	width: 0;
	height: 0;
	border-top: 50px solid transparent;
	border-left: 100px solid red;
	border-bottom: 50px solid transparent;
}
````
![8](https://cloud.githubusercontent.com/assets/5993597/7499842/fce3c12c-f3f7-11e4-9181-ea3932de1cf4.jpg)
##Triangle Top Left
````
#triangle-topleft {
	width: 0;
	height: 0;
	border-top: 100px solid red;
	border-right: 100px solid transparent;
}
````
![9](https://cloud.githubusercontent.com/assets/5993597/7499845/fcf1e4f0-f3f7-11e4-86b8-b5fc0d1b352f.jpg)
##Triangle Top Right
````
#triangle-topright {
	width: 0;
	height: 0;
	border-top: 100px solid red;
	border-left: 100px solid transparent;

}
````
![10](https://cloud.githubusercontent.com/assets/5993597/7499843/fce48fa8-f3f7-11e4-9004-b4c914c99330.jpg)
##Triangle Bottom Left
````
#triangle-bottomleft {
	width: 0;
	height: 0;
	border-bottom: 100px solid red;
	border-right: 100px solid transparent;
}
````	
![11](https://cloud.githubusercontent.com/assets/5993597/7499808/fa5e81a8-f3f7-11e4-8ce3-efc4a4da77d8.jpg)
##Triangle Bottom Right
````
#triangle-bottomright {
	width: 0;
	height: 0;
	border-bottom: 100px solid red;
	border-left: 100px solid transparent;
}
````
![12](https://cloud.githubusercontent.com/assets/5993597/7499809/fa802092-f3f7-11e4-8afb-b9ba40fb24b4.jpg)
##Curved Tail Arrow via Ando Razafimandimby
````
#curvedarrow {
  position: relative;
  width: 0;
  height: 0;
  border-top: 9px solid transparent;
  border-right: 9px solid red;
  -webkit-transform: rotate(10deg);
  -moz-transform: rotate(10deg);
  -ms-transform: rotate(10deg);
  -o-transform: rotate(10deg);
}
#curvedarrow:after {
  content: "";
  position: absolute;
  border: 0 solid transparent;
  border-top: 3px solid red;
  border-radius: 20px 0 0 0;
  top: -12px;
  left: -9px;
  width: 12px;
  height: 12px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
}
````
![13](https://cloud.githubusercontent.com/assets/5993597/7499810/fa9ee11c-f3f7-11e4-933a-661e78434b6f.jpg)
##Trapezoid
````
#trapezoid {
	border-bottom: 100px solid red;
	border-left: 50px solid transparent;
	border-right: 50px solid transparent;
	height: 0;
	width: 100px;
}
````	
![14](https://cloud.githubusercontent.com/assets/5993597/7499812/fabbb1de-f3f7-11e4-826e-9ec728a3de2e.jpg)
##Parallelogram
````
#parallelogram {
	width: 150px;
	height: 100px;
	-webkit-transform: skew(20deg);
	   -moz-transform: skew(20deg);
	     -o-transform: skew(20deg);
	background: red;
}
````
![15](https://cloud.githubusercontent.com/assets/5993597/7499814/fad87e22-f3f7-11e4-8e3e-de39dc773270.jpg)
##Star (6-points)
````
#star-six {
	width: 0;
	height: 0;
	border-left: 50px solid transparent;
	border-right: 50px solid transparent;
	border-bottom: 100px solid red;
	position: relative;
}
#star-six:after {
	width: 0;
	height: 0;
	border-left: 50px solid transparent;
	border-right: 50px solid transparent;
	border-top: 100px solid red;
	position: absolute;
	content: "";
	top: 30px;
	left: -50px;
}
````
![16](https://cloud.githubusercontent.com/assets/5993597/7499815/fb341cc8-f3f7-11e4-9d88-5184a68e3dcd.jpg)
##Star (5-points) via Kit MacAllister
````
#star-five {
   margin: 50px 0;
   position: relative;
   display: block;
   color: red;
   width: 0px;
   height: 0px;
   border-right:  100px solid transparent;
   border-bottom: 70px  solid red;
   border-left:   100px solid transparent;
   -moz-transform:    rotate(35deg);
   -webkit-transform: rotate(35deg);
   -ms-transform:     rotate(35deg);
   -o-transform:      rotate(35deg);
}
#star-five:before {
   border-bottom: 80px solid red;
   border-left: 30px solid transparent;
   border-right: 30px solid transparent;
   position: absolute;
   height: 0;
   width: 0;
   top: -45px;
   left: -65px;
   display: block;
   content: '';
   -webkit-transform: rotate(-35deg);
   -moz-transform:    rotate(-35deg);
   -ms-transform:     rotate(-35deg);
   -o-transform:      rotate(-35deg);

}
#star-five:after {
   position: absolute;
   display: block;
   color: red;
   top: 3px;
   left: -105px;
   width: 0px;
   height: 0px;
   border-right: 100px solid transparent;
   border-bottom: 70px solid red;
   border-left: 100px solid transparent;
   -webkit-transform: rotate(-70deg);
   -moz-transform:    rotate(-70deg);
   -ms-transform:     rotate(-70deg);
   -o-transform:      rotate(-70deg);
   content: '';
}
````
![17](https://cloud.githubusercontent.com/assets/5993597/7499816/fb683ca6-f3f7-11e4-8fd1-56ca069e386d.jpg)
##Pentagon
````
#pentagon {
    position: relative;
    width: 54px;
    border-width: 50px 18px 0;
    border-style: solid;
    border-color: red transparent;
}
#pentagon:before {
    content: "";
    position: absolute;
    height: 0;
    width: 0;
    top: -85px;
    left: -18px;
    border-width: 0 45px 35px;
    border-style: solid;
    border-color: transparent transparent red;
}
````
![18](https://cloud.githubusercontent.com/assets/5993597/7499817/fb85c6c2-f3f7-11e4-8622-6f5257e620d6.jpg)
##Hexagon
````
#hexagon {
	width: 100px;
	height: 55px;
	background: red;
	position: relative;
}
#hexagon:before {
	content: "";
	position: absolute;
	top: -25px;
	left: 0;
	width: 0;
	height: 0;
	border-left: 50px solid transparent;
	border-right: 50px solid transparent;
	border-bottom: 25px solid red;
}
#hexagon:after {
	content: "";
	position: absolute;
	bottom: -25px;
	left: 0;
	width: 0;
	height: 0;
	border-left: 50px solid transparent;
	border-right: 50px solid transparent;
	border-top: 25px solid red;
}
````
![19](https://cloud.githubusercontent.com/assets/5993597/7499818/fba55f6e-f3f7-11e4-8588-7b81e7499d94.jpg)
##Octagon
````
#octagon {
	width: 100px;
	height: 100px;
	background: red;
	position: relative;
}

#octagon:before {
	content: "";
	position: absolute;
	top: 0;
	left: 0;
	border-bottom: 29px solid red;
	border-left: 29px solid #eee;
	border-right: 29px solid #eee;
	width: 42px;
	height: 0;
}

#octagon:after {
	content: "";
	position: absolute;
	bottom: 0;
	left: 0;
	border-top: 29px solid red;
	border-left: 29px solid #eee;
	border-right: 29px solid #eee;
	width: 42px;
	height: 0;
}
````	
![20](https://cloud.githubusercontent.com/assets/5993597/7499819/fbbc34aa-f3f7-11e4-8af3-a88fd367c169.jpg)
##Heart via Nicolas Gallagher
````
#heart {
    position: relative;
    width: 100px;
    height: 90px;
}
#heart:before,
#heart:after {
    position: absolute;
    content: "";
    left: 50px;
    top: 0;
    width: 50px;
    height: 80px;
    background: red;
    -moz-border-radius: 50px 50px 0 0;
    border-radius: 50px 50px 0 0;
    -webkit-transform: rotate(-45deg);
       -moz-transform: rotate(-45deg);
        -ms-transform: rotate(-45deg);
         -o-transform: rotate(-45deg);
            transform: rotate(-45deg);
    -webkit-transform-origin: 0 100%;
       -moz-transform-origin: 0 100%;
        -ms-transform-origin: 0 100%;
         -o-transform-origin: 0 100%;
            transform-origin: 0 100%;
}
#heart:after {
    left: 0;
    -webkit-transform: rotate(45deg);
       -moz-transform: rotate(45deg);
        -ms-transform: rotate(45deg);
         -o-transform: rotate(45deg);
            transform: rotate(45deg);
    -webkit-transform-origin: 100% 100%;
       -moz-transform-origin: 100% 100%;
        -ms-transform-origin: 100% 100%;
         -o-transform-origin: 100% 100%;
            transform-origin :100% 100%;
}
````
![21](https://cloud.githubusercontent.com/assets/5993597/7499820/fbd58680-f3f7-11e4-9547-57efe4e094b9.jpg)
##Infinity via Nicolas Gallagher
````
#infinity {
    position: relative;
    width: 212px;
    height: 100px;
}

#infinity:before,
#infinity:after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 60px;
    height: 60px;
    border: 20px solid red;
    -moz-border-radius: 50px 50px 0 50px;
         border-radius: 50px 50px 0 50px;
    -webkit-transform: rotate(-45deg);
       -moz-transform: rotate(-45deg);
        -ms-transform: rotate(-45deg);
         -o-transform: rotate(-45deg);
            transform: rotate(-45deg);
}

#infinity:after {
    left: auto;
    right: 0;
    -moz-border-radius: 50px 50px 50px 0;
         border-radius: 50px 50px 50px 0;
    -webkit-transform: rotate(45deg);
       -moz-transform: rotate(45deg);
        -ms-transform: rotate(45deg);
         -o-transform: rotate(45deg);
            transform: rotate(45deg);
}
````
![22](https://cloud.githubusercontent.com/assets/5993597/7499821/fbf311f0-f3f7-11e4-8a6c-5fe46eb6a933.jpg)
##Diamond Square via Joseph Silber
````
#diamond {
	width: 0;
	height: 0;
	border: 50px solid transparent;
	border-bottom-color: red;
	position: relative;
	top: -50px;
}
#diamond:after {
	content: '';
	position: absolute;
	left: -50px;
	top: 50px;
	width: 0;
	height: 0;
	border: 50px solid transparent;
	border-top-color: red;
}
````
![23](https://cloud.githubusercontent.com/assets/5993597/7499822/fc1003fa-f3f7-11e4-8d47-4efd6ecbf4f1.jpg)
##Diamond Shield via Joseph Silber
````
#diamond-shield {
	width: 0;
	height: 0;
	border: 50px solid transparent;
	border-bottom: 20px solid red;
	position: relative;
	top: -50px;
}
#diamond-shield:after {
	content: '';
	position: absolute;
	left: -50px; top: 20px;
	width: 0;
	height: 0;
	border: 50px solid transparent;
	border-top: 70px solid red;
}
````
![24](https://cloud.githubusercontent.com/assets/5993597/7499823/fc36b4dc-f3f7-11e4-912a-09eaae46072c.jpg)
##Diamond Narrow via Joseph Silber
````
#diamond-narrow {
	width: 0;
	height: 0;
	border: 50px solid transparent;
	border-bottom: 70px solid red;
	position: relative;
	top: -50px;
}
#diamond-narrow:after {
	content: '';
	position: absolute;
	left: -50px; top: 70px;
	width: 0;
	height: 0;
	border: 50px solid transparent;
	border-top: 70px solid red;
}
````
![25](https://cloud.githubusercontent.com/assets/5993597/7499824/fc563c4e-f3f7-11e4-9d00-1ceed04de49a.jpg)
##Cut Diamond via Alexander Futekov
````
#cut-diamond {
    border-style: solid;
    border-color: transparent transparent red transparent;
    border-width: 0 25px 25px 25px;
    height: 0;
    width: 50px;
    position: relative;
    margin: 20px 0 50px 0;
}
#cut-diamond:after {
    content: "";
    position: absolute;
    top: 25px;
    left: -25px;
    width: 0;
    height: 0;
    border-style: solid;
    border-color: red transparent transparent transparent;
    border-width: 70px 50px 0 50px;
}
````
![26](https://cloud.githubusercontent.com/assets/5993597/7499825/fc7149c6-f3f7-11e4-9265-50755237989f.jpg)
##Egg
````
#egg {
   display:block;
   width: 126px;
   height: 180px;
   background-color: red;
   -webkit-border-radius: 63px 63px 63px 63px / 108px 108px 72px 72px;
   border-radius:         50%  50%  50%  50%  / 60%   60%   40%  40%;
}
````
![27](https://cloud.githubusercontent.com/assets/5993597/7499826/fc7e4ba8-f3f7-11e4-8db0-077b3b9226e6.jpg)
##Pac-Man
````
#pacman {
  width: 0px;
  height: 0px;
  border-right: 60px solid transparent;
  border-top: 60px solid red;
  border-left: 60px solid red;
  border-bottom: 60px solid red;
  border-top-left-radius: 60px;
  border-top-right-radius: 60px;
  border-bottom-left-radius: 60px;
  border-bottom-right-radius: 60px;
}
````
![28](https://cloud.githubusercontent.com/assets/5993597/7499832/fc934dbe-f3f7-11e4-8ba0-191f1dc09395.jpg)
##Talk Bubble
````
#talkbubble {
   width: 120px;
   height: 80px;
   background: red;
   position: relative;
   -moz-border-radius:    10px;
   -webkit-border-radius: 10px;
   border-radius:         10px;
}
#talkbubble:before {
   content:"";
   position: absolute;
   right: 100%;
   top: 26px;
   width: 0;
   height: 0;
   border-top: 13px solid transparent;
   border-right: 26px solid red;
   border-bottom: 13px solid transparent;
}
````
![29](https://cloud.githubusercontent.com/assets/5993597/7499827/fc8e98be-f3f7-11e4-8d8f-f4ffc3f38ee9.jpg)
##12 Point Burst via Alan Johnson
````
#burst-12 {
    background: red;
    width: 80px;
    height: 80px;
    position: relative;
    text-align: center;
}
#burst-12:before, #burst-12:after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    height: 80px;
    width: 80px;
    background: red;
}
#burst-12:before {
    -webkit-transform: rotate(30deg);
       -moz-transform: rotate(30deg);
        -ms-transform: rotate(30deg);
         -o-transform: rotate(30deg);
}
#burst-12:after {
    -webkit-transform: rotate(60deg);
       -moz-transform: rotate(60deg);
        -ms-transform: rotate(60deg);
         -o-transform: rotate(60deg);
}
````
![30](https://cloud.githubusercontent.com/assets/5993597/7499828/fc8ef21e-f3f7-11e4-8e22-8992d3a5b465.jpg)
##8 Point Burst via Alan Johnson
````
#burst-8 {
    background: red;
    width: 80px;
    height: 80px;
    position: relative;
    text-align: center;
    -webkit-transform: rotate(20deg);
       -moz-transform: rotate(20deg);
        -ms-transform: rotate(20deg);
         -o-transform: rotate(20eg);
}
#burst-8:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    height: 80px;
    width: 80px;
    background: red;
    -webkit-transform: rotate(135deg);
       -moz-transform: rotate(135deg);
        -ms-transform: rotate(135deg);
         -o-transform: rotate(135deg);
}
````
![31](https://cloud.githubusercontent.com/assets/5993597/7499829/fc8f015a-f3f7-11e4-975c-cae7fc15327e.jpg)
##Yin Yang via Alexander Futekov
````
#yin-yang {
	width: 96px;
	height: 48px;
	background: #eee;
	border-color: red;
	border-style: solid;
	border-width: 2px 2px 50px 2px;
	border-radius: 100%;
	position: relative;
}

#yin-yang:before {
	content: "";
	position: absolute;
	top: 50%;
	left: 0;
	background: #eee;
	border: 18px solid red;
	border-radius: 100%;
	width: 12px;
	height: 12px;
}

#yin-yang:after {
	content: "";
	position: absolute;
	top: 50%;
	left: 50%;
	background: red;
	border: 18px solid #eee;
	border-radius:100%;
	width: 12px;
	height: 12px;
}
````
![32](https://cloud.githubusercontent.com/assets/5993597/7499830/fc8f8e54-f3f7-11e4-8afe-e983de1f017e.jpg)
##Badge Ribbon via Catalin Rosu
````
#badge-ribbon {
 position: relative;
 background: red;
 height: 100px;
 width: 100px;
 -moz-border-radius:    50px;
 -webkit-border-radius: 50px;
 border-radius:         50px;
}

#badge-ribbon:before,
#badge-ribbon:after {
  content: '';
  position: absolute;
  border-bottom: 70px solid red;
  border-left: 40px solid transparent;
  border-right: 40px solid transparent;
  top: 70px;
  left: -10px;
  -webkit-transform: rotate(-140deg);
  -moz-transform:    rotate(-140deg);
  -ms-transform:     rotate(-140deg);
  -o-transform:      rotate(-140deg);
}

#badge-ribbon:after {
  left: auto;
  right: -10px;
  -webkit-transform: rotate(140deg);
  -moz-transform:    rotate(140deg);
  -ms-transform:     rotate(140deg);
  -o-transform:      rotate(140deg);
}
````
![33](https://cloud.githubusercontent.com/assets/5993597/7499831/fc91da7e-f3f7-11e4-82fd-ac6ae0327e6e.jpg)
##Space Invader via Vlad Zinculescu
````
#space-invader{

  box-shadow:
    0 0 0 1em red,
    0 1em 0 1em red,
    -2.5em 1.5em 0 .5em red,
    2.5em 1.5em 0 .5em red,
    -3em -3em 0 0 red,
    3em -3em 0 0 red,
    -2em -2em 0 0 red,
    2em -2em 0 0 red,
    -3em -1em 0 0 red,
    -2em -1em 0 0 red,
    2em -1em 0 0 red,
    3em -1em 0 0 red,
    -4em 0 0 0 red,
    -3em 0 0 0 red,
    3em 0 0 0 red,
    4em 0 0 0 red,
    -5em 1em 0 0 red,
    -4em 1em 0 0 red,
    4em 1em 0 0 red,
    5em 1em 0 0 red,
    -5em 2em 0 0 red,
    5em 2em 0 0 red,
    -5em 3em 0 0 red,
    -3em 3em 0 0 red,
    3em 3em 0 0 red,
    5em 3em 0 0 red,
    -2em 4em 0 0 red,
    -1em 4em 0 0 red,
    1em 4em 0 0 red,
    2em 4em 0 0 red;

    background: red;
    width: 1em;
    height: 1em;
    overflow: hidden;

    margin: 50px 0 70px 65px;
  }
````
![34](https://cloud.githubusercontent.com/assets/5993597/7499833/fc9c25e2-f3f7-11e4-8194-da187363ebcc.jpg)
##TV Screen
````
#tv {
  position: relative;
  width: 200px;
  height: 150px;
  margin: 20px 0;
  background: red;
  border-radius: 50% / 10%;
  color: white;
  text-align: center;
  text-indent: .1em;
}
#tv:before {
  content: '';
  position: absolute;
  top: 10%;
  bottom: 10%;
  right: -5%;
  left: -5%;
  background: inherit;
  border-radius: 5% / 50%;
}
````
![35](https://cloud.githubusercontent.com/assets/5993597/7499835/fc9fddc2-f3f7-11e4-8bd0-5db6c3b9171e.jpg)
##Chevron via Anthony Ticknor
````
#chevron {
  position: relative;
  text-align: center;
  padding: 12px;
  margin-bottom: 6px;
  height: 60px;
  width: 200px;
}

#chevron:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 51%;
  background: red;
  -webkit-transform: skew(0deg, 6deg);
  -moz-transform: skew(0deg, 6deg);
  -ms-transform: skew(0deg, 6deg);
  -o-transform: skew(0deg, 6deg);
  transform: skew(0deg, 6deg);
}
#chevron:after {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  height: 100%;
  width: 50%;
  background: red;
  -webkit-transform: skew(0deg, -6deg);
  -moz-transform: skew(0deg, -6deg);
  -ms-transform: skew(0deg, -6deg);
  -o-transform: skew(0deg, -6deg);
  transform: skew(0deg, -6deg);
}​
````
![36](https://cloud.githubusercontent.com/assets/5993597/7499834/fc9debac-f3f7-11e4-90e2-223dd80aeb63.jpg)
##Magnifying Glass
````
#magnifying-glass
{
 font-size: 10em; /* This controls the size. */
 display: inline-block;
 width: 0.4em;
 height: 0.4em;
 border: 0.1em solid red;
 position: relative;
 border-radius: 0.35em;
}
#magnifying-glass::before
{
 content: "";
 display: inline-block;
 position: absolute;
 right: -0.25em;
 bottom: -0.1em;
 border-width: 0;
 background: red;
 width: 0.35em;
 height: 0.08em;
 -webkit-transform: rotate(45deg);
    -moz-transform: rotate(45deg);
     -ms-transform: rotate(45deg);
      -o-transform: rotate(45deg);
}
````     
![37](https://cloud.githubusercontent.com/assets/5993597/7499836/fc9ff1a4-f3f7-11e4-9f63-8f02d84e9423.jpg)
##Facebook Icon via Nathan Swartz
```` 
#facebook-icon {
  background: red;
  text-indent: -999em;
  width: 100px;
  height: 110px;
  border-radius: 5px;
  position: relative;
  overflow: hidden;
  border: 15px solid red;
  border-bottom: 0;
}
#facebook-icon::before {
  content: "/20";
  position: absolute;
  background: red;
  width: 40px;
  height: 90px;
  bottom: -30px;
  right: -37px;
  border: 20px solid #eee;
  border-radius: 25px;
}
#facebook-icon::after {
  content: "/20";
  position: absolute;
  width: 55px;
  top: 50px;
  height: 20px;
  background: #eee;
  right: 5px;
}
````  
![38](https://cloud.githubusercontent.com/assets/5993597/7499837/fca31db6-f3f7-11e4-9a97-4746f40c596c.jpg)
##Cone via Omid Rasouli
````
#cone {
  width: 0;
  height: 0;
  border-left: 70px solid transparent;
  border-right: 70px solid transparent;
  border-top: 100px solid red;
  -moz-border-radius: 50%;
  -webkit-border-radius: 50%;
  border-radius: 50%;
}
````    
![39](https://cloud.githubusercontent.com/assets/5993597/7499840/fcb143f0-f3f7-11e4-9055-3709ea9198de.jpg)
##Moon via Omid Rasouli
````
#moon {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  box-shadow: 15px 15px 0 0 red;
}
````        
![40](https://cloud.githubusercontent.com/assets/5993597/7499838/fcb0a0b2-f3f7-11e4-8002-5f3b4b74ec3f.jpg)
##Flag via Zoe Rooney
````
#flag {
  width: 110px;
  height: 56px;
  padding-top: 15px;
  position: relative;
  background: red;
  color: white;
  font-size: 11px;
  letter-spacing: 0.2em;
  text-align: center;
  text-transform: uppercase;
}
#flag:after {
  content: "";
  position: absolute;
  left: 0;
  bottom: 0;
  width: 0;
  height: 0;
  border-bottom: 13px solid #eee;
  border-left: 55px solid transparent;
  border-right: 55px solid transparent;
}
````      
![41](https://cloud.githubusercontent.com/assets/5993597/7499839/fcb0dd8e-f3f7-11e4-821f-c1b1d8f694ca.jpg)
##Cross via Kaya Basharan
````
#cross {
  background: red;
  height: 100px;
  position: relative;
  width: 20px;
}
#cross:after {
  background: red;
  content: "";
  height: 20px;
  left: -40px;
  position: absolute;
  top: 40px;
  width: 100px;
}
````  
![43](https://cloud.githubusercontent.com/assets/5993597/7499853/03a067fe-f3f8-11e4-9818-f1aa60b623b5.jpg)
##Base via Josh Rodgers
````
#base {
  background: red;
  display: inline-block;
  height: 55px;
  margin-left: 20px;
  margin-top: 55px;
    position: relative;
    width: 100px;
}
#base:before {
  border-bottom: 35px solid red;
  border-left: 50px solid transparent;
  border-right: 50px solid transparent;
  content: "";
  height: 0;
  left: 0;
  position: absolute;
  top: -35px;
  width: 0;
}
````
![44](https://cloud.githubusercontent.com/assets/5993597/7499852/039d521c-f3f8-11e4-90a8-8db306953d2c.jpg)
