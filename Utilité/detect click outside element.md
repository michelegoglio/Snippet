````
 function detectClickOutsideElement() {
	$("body").click(function(e) {
		if( $("TSTooltip").hasClass("active")){
	 		if (!(e.target == "TSTooltipTrigger" || $(e.target).parents("TSTooltipTrigger").size())) {
	  			$("TSTooltip").removeClass("active");
			}
		}
	});
}
````
