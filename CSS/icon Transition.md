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
		<script>
			$(function() {
				$("#menuIcon,#arrowIcon").on("click", function() {
				    $(this).toggleClass("active");
				});

			  $('#td3controls #td3xrot').change(function () {
			      $('#cube').css("transform","rotateX("+$('#td3controls input#td3xrot').val()+"deg)");
			      $('label[for="td3xrot"]').html("X rotation ("+$('#td3controls input#td3xrot').val()+" deg)")
			  });
			  $('#td3controls #td3yrot').change(function () {
			      $('#Ycube').css("transform","rotateY("+$('#td3controls input#td3yrot').val()+"deg)");
			      $('label[for="td3yrot"]').html("Y rotation ("+$('#td3controls input#td3yrot').val()+" deg)")
			  });
			  $('#td3controls #td3zrot').change(function () {
			      $('#Zcube').css("transform","rotateZ("+$('#td3controls input#td3zrot').val()+"deg)");
			      $('label[for="td3zrot"]').html("Z rotation ("+$('#td3controls input#td3zrot').val()+" deg)")
			  });
			  $('#td3controls #td3perspective').change(function () {
			      $('#transDemo3').css("perspective",$('#td3controls input#td3perspective').val()+"px");
			      $('label[for="td3perspective"]').html("Perspective ("+$('#td3controls input#td3perspective').val()+" px)")
			  });
			});
		</script>		
	</body>
</html>
````

mixins.less
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
````

default.less
````
@import "mixins";

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

#transDemo3 {
	-webkit-perspective: 800px;
	-webkit-perspective-origin: 50% 100px;
	-moz-perspective: 800px;
	-moz-perspective-origin: 50% 100px;
	-ms-perspective: 800px;
	-ms-perspective-origin: 50% 100px;
	perspective: 800px;
	perspective-origin: 50% 100px;
	margin:50px auto;
	width:400px;
	float:left;
	#Ycube,
	#Zcube {
		-webkit-transform-style: preserve-3d;
		-moz-transform-style: preserve-3d;
		-ms-transform-style: preserve-3d;
		transform-style: preserve-3d;		
		#cube {
			position: relative;
			margin: 0 auto;
			height: 200px;
			width: 200px;
			-webkit-transform-style: preserve-3d;
			-webkit-transform-origin: 50% 100px 0;
			-moz-transform-style: preserve-3d;
			-moz-transform-origin: 50% 100px 0;
			-ms-transform-style: preserve-3d;
			-ms-transform-origin: 50% 100px 0;
			transform-style: preserve-3d;
			transform-origin: 50% 100px 0;
			.face {
				position: absolute;
				height: 160px;
				width: 160px;
				padding: 20px;
				background-color: rgba(50, 50, 50, 0.3);
				-webkit-backface-visibility: visible;
				-moz-backface-visibility: visible;
				-ms-backface-visibility: visible;
				backface-visibility: visible;
				border:1px #aaa solid;
				p {
					font-size:160px;
					line-height:1;
					text-align:center;
					margin:0;
					padding:0;
					color:rgba(0,0,0,0.75);
				}
				&.one  {
					-webkit-transform: rotateX(90deg) translateZ(100px);
					-moz-transform: rotateX(90deg) translateZ(100px);
					-ms-transform: rotateX(90deg) translateZ(100px);
					transform: rotateX(90deg) translateZ(100px);
					background-color: rgba(255, 0, 0, 0.5);
				}
				&.two {
					-webkit-transform: translateZ(100px);
					-moz-transform: translateZ(100px);
					-ms-transform: translateZ(100px);
					transform: translateZ(100px);
				}

				&.three {
					-webkit-transform: rotateY(90deg) translateZ(100px);
					-moz-transform: rotateY(90deg) translateZ(100px);
					-ms-transform: rotateY(90deg) translateZ(100px);
					transform: rotateY(90deg) translateZ(100px);
				}

				&.four {
					-webkit-transform: rotateY(180deg) translateZ(100px);
					-moz-transform: rotateY(180deg) translateZ(100px);
					-ms-transform: rotateY(180deg) translateZ(100px);
					transform: rotateY(180deg) translateZ(100px);
					background-color: rgba(0, 255, 0, 0.5);
				}

				&.five {
					-webkit-transform: rotateY(-90deg) translateZ(100px);
					-moz-transform: rotateY(-90deg) translateZ(100px);
					-ms-transform: rotateY(-90deg) translateZ(100px);
					transform: rotateY(-90deg) translateZ(100px);
				}

				&.six {
					-webkit-transform: rotateX(-90deg) translateZ(100px) rotate(180deg);
					-moz-transform: rotateX(-90deg) translateZ(100px) rotate(180deg);
					-ms-transform: rotateX(-90deg) translateZ(100px) rotate(180deg);
					transform: rotateX(-90deg) translateZ(100px) rotate(180deg);
					background-color: rgba(0, 0, 255, 0.5);
				}				
			}
		}
	}
}

#td3controls {
	width:290px;
	float:right;
	label,
	input {
		float:left;
		width:100%;
	}
}
````
