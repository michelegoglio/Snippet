#Icone transition

*HTML*

````
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8"> 
		<link rel="stylesheet" type="text/css" href="default.css" />
		<script type="text/javascript" src="https://code.jquery.com/jquery-2.1.1.min.js"></script>
	</head>
	<body>
		<a id="arrowIcon" class="icon" href="#"><span></span></a>
		<a id="arrowIconHover" class="icon" href="#"><span></span></a>
		
		<a id="menuIcon" class="icon" href="#"><span></span></a>
	</body>
</html>	
````

*styles*
````
.mixins-rotate(@rotationDegree){
	-moz-transform: rotate(@rotationDegree);
	-webkit-transform: rotate(@rotationDegree);
	-o-transform: rotate(@rotationDegree);
	-ms-transform: rotate(@rotationDegree);
	transform: rotate(@rotationDegree);
}

.mixins-transition(@delay,@effect){
	-moz-transition: all @delay @effect;
	-webkit-transition: all @delay @effect;
	-o-transition: all @delay @effect;
	-ms-transition: all @delay @effect;
	transition: all @delay @effect;	
}

.mixins-scale2d(@scaleX,@scaleY){
	-moz-transform: scale(@scaleX,@scaleY);
	-webkit-transform: scale(@scaleX,@scaleY);
	-o-transform: scale(@scaleX,@scaleY);
	-ms-transform: scale(@scaleX,@scaleY);	
	transform:scale(@scaleX,@scaleY);
}

@-webkit-keyframes iconTransformation {
    25%  {.mixins-scale2d(0.5,0.5);}
    50%  {.mixins-rotate(180deg);}
    75%  {.mixins-scale2d(1,1);}
    100% {.mixins-paused();}
}
@keyframes iconTransformation {
    25%  {.mixins-scale2d(0.5,0.5);}
    50%  {.mixins-rotate(180deg);}
    75%  {.mixins-scale2d(1,1);}
    100% {.mixins-paused();}
}

.mixins-paused(){
    -webkit-animation-play-state:paused;
    -moz-animation-play-state:paused;
    -o-animation-play-state:paused; 
    animation-play-state:paused;
}



.mixins-keyframe-animation(@animationName,@delay){
	-webkit-animation: @animationName @delay; 
    animation: @animationName @delay;	
}

body { 
	background-color: black; 
	height: 100%; 
}

.icon{
	cursor: pointer; 
	padding: 10px 35px 16px 0px;
	position: absolute; 
	span:before,
	span:after{
	  cursor: pointer;
	  border-radius: 1px;
	  height: 5px;
	  width: 35px;
	  background: white;
	  position: absolute;
	  display: block;
	  content: '';
	  transition: all 500ms ease-in-out;
	 }
}
#menuIcon { 
	left: 50%; 
	top: 50%; 	
	span{
	  cursor: pointer;
	  border-radius: 1px;
	  height: 5px;
	  width: 35px;
	  background: white;
	  position: absolute;
	  display: block;
	  content: '';
	  transition: all 500ms ease-in-out;		
		&:before{
			top: -10px; 
		}
		&:after {
		  bottom: -10px;
		}
	}
	&.active{
		span {
		  background-color: transparent;
		  &:before,
		  &:after{
			top: 0;
		  }
		  &:before{
		  	transform: rotate(45deg);
		  }
		  &:after{
		  	transform: rotate(-45deg);
		  }					  
		}
	}
}

#arrowIcon { 
	&.icon{
		.mixins-transition(0.5s,ease-in-out);
		left: 30%; 
		top: 30%; 	
		span{
			&:before,
			&:after{
				width: 25px;
				top: 5px;
			}
			&:before{
				left:-5%;
				transform: rotate(-45deg);
			}
			&:after {
				transform: rotate(45deg);
				right:-5%;
			}
		}
		&.active{
			span {
			  background-color: transparent;
				&:before,
				&:after{
					top: 15px;
				}		  
				&:before{
				  	transform: rotate(45deg);
				}
			  	&:after{
			  		transform: rotate(-45deg);
			  	}					  
			}
		}
	}
}
#arrowIconHover { 
	&.icon{
		left: 60%; 
		top: 60%; 	
		span{
			&:before,
			&:after{
				width: 25px;
				top: 5px;
			}
			&:before{
				left:-5%;
				transform: rotate(-45deg);
			}
			&:after {
				transform: rotate(45deg);
				right:-5%;
			}
		}
		&:hover{
			.mixins-keyframe-animation(iconTransformation,1s);
		}	
	}
}
````
