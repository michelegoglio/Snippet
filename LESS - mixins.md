````
.mixins-appearance(){
   -webkit-appearance: none;
   -moz-appearance:    none;
   appearance:         none;
}

.mixins-backface-visibility(@property){
  -webkit-backface-visibility: @property;
  -moz-backface-visibility: @property;
  -ms-backface-visibility: @property;
  -o-backface-visibility: @property;
  backface-visibility: @property;
}

.mixin-background-opacity(@r,@v,@b,@opacity,@defaultColor) {
	background-color: @defaultColor;
	background: rgba(@r,@v,@b,@opacity);
}

.mixins-border-radius(@string){
	-webkit-border-radius: @string;
	-moz-border-radius: @string;
	border-radius: @string;	
}

.mixins-border-bottom-left-radius(@string){
	-webkit-border-bottom-left-radius: @string;
	-moz-border-bottom-left-radius: @string;
	border-bottom-left-radius: @string;	
}

.mixins-border-bottom-right-radius(@string){
	-webkit-border-bottom-right-radius: @string;
	-moz-border-bottom-right-radius: @string;
	border-bottom-right-radius: @string;	
}

.mixins-border-top-right-radius(@string){
	-webkit-border-top-right-radius: @string;
	-moz-border-top-right-radius: @string;
	border-top-right-radius: @string;	
}

.mixins-border-top-left-radius(@string){
	-webkit-border-top-left-radius: @string;
	-moz-border-top-left-radius: @string;
	border-top-left-radius: @string;	
}

.mixins-box-sizing(@style){
	  -webkit-box-sizing: @style;
	  -moz-box-sizing: @style;
	  -ms-box-sizing: @style;
	  -o-box-sizing: @style;  
	  box-sizing: @style;
}

.mixins-ellipsis(@width){
	overflow:hidden;
	text-overflow:ellipsis;
	white-space:nowrap;
	width:@width;
}

.mixins-perspective(@x){
  -webkit-perspective: @x;
    -moz-perspective:  @x;    
    -ms-perspective:  @x;    
    -o-perspective:  @x;
    perspective:  @x;  
}

.mixins-placeholder{
	::-webkit-input-placeholder { /* WebKit browsers */
		color:@color-border;
	}
	:-moz-placeholder { /* Mozilla Firefox 4 to 18 */
	   color:@color-border;
	   opacity:1;
	}
	::-moz-placeholder { /* Mozilla Firefox 19+ */
	   color:@color-border;
	   opacity:1;
	}
	:-ms-input-placeholder { /* Internet Explorer 10+ */
	   color:@color-border;
	}
}

.mixins-rotate(@degrees,@m11,@m12,@m21,@m22){
 	-moz-transform: rotate(@degrees);
  	-webkit-transform: rotate(@degrees);
  	-o-transform: rotate(@degrees);
  	-ms-transform: rotate(@degrees);
	 transform: rotate(@degrees);
	 -ms-filter: "progid:DXImageTransform.Microsoft.Matrix(M11=@m11, M12=@m12, M21=@m21, M22=@m22,sizingMethod='auto expand')";
	 filter: progid:DXImageTransform.Microsoft.Matrix(M11=@m11, M12=@m12, M21=@m21, M22=@m22,sizingMethod='auto expand');
}
	.mixins-rotate(180deg,-1.00000000,-0.00000000,0.00000000,-1.00000000);
	http://www.boogdesign.com/examples/transforms/matrix-calculator.html

.mixins-slide-animation(@duration){
    -webkit-transition: left @duration;
    -moz-transition: left @duration;
    -o-transition: left @duration;
    -ms-transition: left @duration;
    transition: left @duration;
}

.mixins-tap-highlight(@col1,@col2,@col3,@opacity){
	-webkit-tap-highlight-color: rgba(@col1,@col2,@col3,@opacity);
	-webkit-tap-highlight-color: transparent;
}

.mixin-transform-translate3d(@x,@y,@z){
	  -webkit-transform: translate3d(@x,@y,@z);
	  transform: translate3d(@x,@y,@z);
}

.mixins-transform-translateX(@X){
	   -webkit-transform: translateX(@X);
	  -moz-transform: translateX(@X);
	  -ms-transform: translateX(@X);
	  -o-transform: translateX(@X);
	  transform: translateX(@X);
}

.mixins-transition(@duration){
	  -webkit-transition: all @duration ease-in;
	  -moz-transition: all @duration ease-in;
	  -o-transition: all @duration ease-in;
	  -ms-transition: all @duration ease-in;
	  transition: all @duration ease-in;
}

.mixins-transition-delay(@delay){
	  -webkit-transition: @delay;
	  -moz-transition: @delay;
	  -o-transition: @delay;
	  -ms-transition: @delay;
	  transition: @delay;
}

.mixins-transition-duration(@duration){
	-webkit-transition-duration: @duration;
	-moz-transition-duration: @duration;
	-o-transition-duration: @duration;
	-ms-transition-duration: @duration;
	transition-duration: @duration;
}

.mixins-transition-vertical(@duration,@timing,@position){
	-webkit-transition-duration: @duration;
	-moz-transition-duration: @duration;
	-o-transition-duration: @duration;
	-ms-transition-duration: @duration;
	transition-duration: @duration;

	-webkit-transition-timing-function: @timing;
	-moz-transition-timing-function: @timing;
	-o-transition-timing-function: @timing;
	-ms-transition-timing-function: @timing;
	transition-timing-function: @timing;
  
	top:@position;
}

.mixins-transition-vertical-inverse(@duration,@timing,@position){
	-webkit-transition-duration: @duration;
  	-moz-transition-duration: @duration;
  	-o-transition-duration: @duration;
	-ms-transition-duration: @duration;
	transition-duration: @duration;

	-webkit-transition-timing-function: @timing;
	-moz-transition-timing-function: @timing;
	-o-transition-timing-function: @timing;
	-ms-transition-timing-function: @timing;
  	transition-timing-function: @timing;

	bottom:@position;
}

.mixins-transition-horizontal(@duration,@timing,@position){
	-webkit-transition-duration: @duration;
  	-moz-transition-duration: @duration;
  	-o-transition-duration: @duration;
	-ms-transition-duration: @duration;
	transition-duration: @duration;

	-webkit-transition-timing-function: @timing;
  	-moz-transition-timing-function: @timing;
  	-o-transition-timing-function: @timing;
	-ms-transition-timing-function: @timing;
  	transition-timing-function: @timing;

	left:@position;
}

.mixins-transition-cubic-bezier(@p1,@p2,@p3,@p4,@duration){
  	-webkit-transition:all cubic-bezier(@p1,@p2,@p3,@p4) @duration;
	-moz-transition:all cubic-bezier(@p1,@p2,@p3,@p4) @duration;
  	-o-transition:all cubic-bezier(@p1,@p2,@p3,@p4) @duration;
  	transition:all cubic-bezier(@p1,@p2,@p3,@p4) @duration;
}

.mixin-transition-3d(@x,@y,@z,@duration,@val1,@val2,@val3,@opacity) {
    	-webkit-transform: translate3d(@x, @y, @z);
    	opacity: @opacity;
    	-webkit-transition: -webkit-transform @duration cubic-bezier(@val1, @val2, @val3, @opacity), opacity;
    	transition: -webkit-transform @duration cubic-bezier(@val1,@val2, @val3, @opacity), opacity;
}

.mixin-transition-visibility(@opacity,@visibility,@duration) {
    	opacity: @opacity;
    	visibility: hidden;
    	-webkit-transition: visibility @visibility linear @duration,opacity @duration linear;
    	-moz-transition: visibility @visibility linear @duration,opacity @duration linear;
    	-o-transition: visibility @visibility linear @duration,opacity @duration linear;
    	transition: visibility @visibility linear @duration,opacity @duration linear;
}

.mixins-turnOff-webkitAppearance(){
	-webkit-appearance: none;
	border-radius: 0;
}

.mixin-user-select(){
	-webkit-touch-callout: none;
	-webkit-user-select: none;
	-khtml-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none; 
}
````
