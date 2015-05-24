````
- ElementToHide
- TriggerOnClick

 function detectClickOutsideElement() {
	$("body").click(function(e) {
		if( $("ElementToHide").hasClass("active")){
	 		if (!(e.target == "TriggerOnClick" || $(e.target).parents("TriggerOnClick").size())) {
	  			$("ElementToHide").removeClass("active");
			}
		}
	});
}
````
