#Reset btn in html5 && delete IE native icon

**required on input[type="text"] & placeholder attribute, button type="reset"**

````
<div class="search-wrapper">
	<form>
	  <input type="text" name="focus" required placeholder="Enter search term" />
		<button class="btn resetn" type="reset"></button>
	</form>
</div>

input[type="text"],
.btn.reset,
.search-wrapper {
	position: relative;
	padding: 10px;
}
.search-wrapper {
	width: 500px;
	margin: auto;
	margin-top: 50px;
	input[type="text"] {
		width: 80%;
		border: 1px solid #ccc;
	  	outline: 0;
	  	border-radius: 15px;
		&:required,
		&:focus{
			border: none;
			box-shadow:none;
		}
		&:not(:valid) ~ .close-icon {
			display: none;
		}
		&::-ms-clear{
		    display:none; /* IE */
		}		
	}
	.btn.reset{
		border:1px solid transparent;
		background-color: transparent;
		display: inline-block;
		vertical-align: middle;
	  	outline: 0;
	  	cursor: pointer;
		&:after {
			content: "X";
			display: block;
			width: 15px;
			height: 15px;
			position: absolute;
			background-color: #FA9595;
			z-index:1;
			right: 35px;
			top: 0;
			bottom: 0;
			margin: auto;
			padding: 2px;
			border-radius: 50%;
			text-align: center;
			color: white;
			font-weight: normal;
			font-size: 12px;
			box-shadow: 0 0 2px #E50F0F;
			cursor: pointer;
		}	  	
	}	
}
```'
