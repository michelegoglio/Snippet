#3D cube animation 
*HTML*

````
<!DOCTYPE html>
<html>
<head>
	<title></title>
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
