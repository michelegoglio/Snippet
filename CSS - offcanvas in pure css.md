# structure
````
<!DOCTYPE html>
<html>
    <head>
         <meta name="viewport" content="width=device-width, user-scalable=yes, initial-scale=1.0, minimum-scale=1.0">
    </head>
    <body>
        <div class="mediazoneWrapper">
            <div class="mediazone" id="offcanvasMediazone">
                <div class="mediazoneEngine" id="offcanvasAside">
                    mediazone engine
                  <a href="#" class="btn back">back</a>
                </div>
                <div class="mediazoneGallery">
                    <h1 class="titleInfo">
                        <div class="titleInfoInner">
                            <a href="#offcanvasMediazone" class="btn book whiteRabbit">Book a vacation</a>
                        </div>  
                    </h1>
                    <div class="mediazoneTabContent">
                        media zone content
                    </div>
                </div>
            </div>
        </div>
    </body>
</html>
````

#CSS
````
@import "mediaZone-variables";
@import "mediaZone-mixins";
body,
html{
	margin:0;
	padding:0;
}

h1{
background-color: rgba(255, 255, 255, 0.9);
  color: #00367d;
  font-size: 14px;
  font-weight: normal;
  left: 0;
  margin: 0;
  min-height: 60px;
  position: absolute;
  top: 0;
  width: 100%;
  z-index: 10;
}
.mediazoneWrapper {
	height:448px; /*temporaire*/
	overflow: hidden;
	position: relative;
	width: 100%;
	.mediazone {
	  	height: 100%;
	  	position: relative;
	  	width: 100%;
		.mixins-transform-translateX(0);
	  	.mixin-transform-translate3d(0, 0, 0);
	  	.mixins-transition(0.3s);
		.mixins-backface-visibility(hidden);
		.mediazoneEngine {
			height: 100%;
			right: -300px;
			position: absolute;
			top: 0;
			width: 300px;
		  	.mixins-box-sizing(border-box);
			#offcanvasAside .back{
			    bottom:auto;
			  	cursor: pointer;
			  	display: none;			    
			    height:50px;
			    position:static;
			    left:auto;
			    right:auto;
			}
		}	
		.mediazoneGallery{ 
			position: relative; 
			.book{
			    cursor: pointer; 
			    position: absolute; 
			    right:10px;
			    top:0;
			}			
		}
		&#offcanvasMediazone:target .back { 
		    display: block;
		    z-index:1000;
		}		
	}
	.mediazone--active,
	#offcanvasMediazone:target {
		.mixins-transform-translateX(-300px);
		.mixin-transform-translate3d(-300px, 0, 0);
	}	

}
.mediazoneTabContent { }
````
