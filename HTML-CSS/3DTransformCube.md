````
<!DOCTYPE html>
<html>
<head>
	<title>Codeyourweb - Initiation CSS 3D Tranform - Cube 3D | www.codeyourweb.org</title>
	<meta charset="utf-8" />
	<link rel="stylesheet" type="text/css" href="style.css" />
	<script type="text/javascript" src="modernizer.js"></script>
	<script type="text/javascript">
		if (!Modernizr.csstransforms3d) {
			alert("Votre navigateur n'est pas compatible avec les transformations 3D en CSS");
		}

		if(!Modernizr.cssanimations){
			alert('Votre navigateur ne supporte pas les animations en CSS');
		}
	</script>
</head>
<body>
	<p class="indic">Passez votre souris sur le cube pour le disloquer</p>
	<section class="container">
		<div class="cube">
			<figure class="front"><p>FRONT</p></figure>
			<figure class="left"><p>LEFT</p></figure>
			<figure class="right"><p>RIGHT</p></figure>
			<figure class="top"><p>TOP</p></figure>
			<figure class="bottom"><p>BOTTOM</p></figure>
			<figure class="back"><p>BACK</p></figure>
		</div>
	</section>
</body>
</html>
````
````
		p{
			font-family: Arial, Verdana, sans-serif;
			font-size: 1.4em;
		}

		.indic{
			position: absolute;
			bottom: 20px;
			right: 20px;
		}

		.container{
			perspective: 800px;
			perspective-origin: 50% 50%;
			position: absolute;
			left: 20%;
			top: 20%;
		}

		@keyframes rotate{
			from{ transform: rotateY(0deg) rotateX(0deg); }
			to { transform: rotateY(360deg) rotateX(360deg); }
		}


		@-webkit-keyframes webkitRotate{
			from{ -webkit-transform: rotateY(0deg) rotateX(0deg); }
			to { -webkit-transform: rotateY(360deg) rotateX(360deg); }
		}


		.cube{
			position: relative;
			transform-style: preserve-3d;
			width: 200px;
			height: 200px;
			animation: rotate 15s infinite linear;
			-webkit-animation: webkitRotate 15s infinite linear;
		}

		div figure{
			border: #000 3px solid;
			position: absolute;
			height: 200px;
			width: 200px;
			padding: 0px;
			margin: 0px;
			background-color: #a90329;
			box-sizing: border-box;
		}

		div figure p{
			margin: 40% auto;
			text-align: center;
		}

		.cube:hover figure{
				background-color: #a90329;
				background: -moz-linear-gradient(top,  #a90329 0%, #8f0222 83%, #6d0019 100%);
				background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#a90329), color-stop(83%,#8f0222), color-stop(100%,#6d0019));
				background: -webkit-linear-gradient(top,  #a90329 0%,#8f0222 83%,#6d0019 100%);
				background: -o-linear-gradient(top,  #a90329 0%,#8f0222 83%,#6d0019 100%);
				background: -ms-linear-gradient(top,  #a90329 0%,#8f0222 83%,#6d0019 100%);
				background: linear-gradient(to bottom,  #a90329 0%,#8f0222 83%,#6d0019 100%);
				filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#a90329', endColorstr='#6d0019',GradientType=0 );
		}

		.left{ transform: rotateY(-90deg) translateZ(100px); }
		.right{ transform: rotateY(90deg) translateZ(100px); }
		.top{ transform: rotateX(90deg) translateZ(100px); }
		.bottom{ transform: rotateX(-90deg) translateZ(100px); }
		.front{ transform: rotateY(0deg) translateZ( 100px ); }
		.back{ transform: rotateY(180deg) translateZ(100px); }

		.cube:hover .front{ transform: translateZ(150px)}
		.cube:hover .back{ transform: translateZ(-150px);}
		.cube:hover .right{ transform: rotateY(90deg) translateZ(150px);}
		.cube:hover .left{ transform: rotateY(-90deg) translateZ(150px); }
		.cube:hover .top{ transform: rotateX(90deg) translateZ(150px);}
		.cube:hover .bottom{ transform: rotateX(-90deg) translateZ(150px);}

````
