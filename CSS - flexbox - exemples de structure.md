#1er exemple
##html
````
<div class="flexbox-parent">
    <div class="flexbox-item header">
        Header
    </div>
    
    <div class="flexbox-item fill-area content flexbox-item-grow">
        <div class="fill-area-content flexbox-item-grow">
            Content 
            <br /><br />
            Emulates height 100% with a horizontal flexbox with stretch
            <br /><br />      
            This box with a border should fill the blue area except for the padding (just to show the middle flexbox item).
        </div>
    </div>
    
    <div class="flexbox-item footer">
        Footer
    </div>
</div>

````

##styles
````
*, *:before, *:after
{
	-moz-box-sizing: border-box;
	-webkit-box-sizing: border-box;
	box-sizing: border-box;
}

html, body
{
    width: 100%;
    height: 100%;
    
    margin: 0;
    padding: 0;
}

body
{
    background: #444444;
    
    color: #cccccc;
    font-size: 14px;
    /* Helvetica/Arial-based sans serif stack */
    font-family: Frutiger, "Frutiger Linotype", Univers, Calibri, "Gill Sans", "Gill Sans MT", "Myriad Pro", Myriad, "DejaVu Sans Condensed", "Liberation Sans", "Nimbus Sans L", Tahoma, Geneva, "Helvetica Neue", Helvetica, Arial, sans-serif;

}

.flexbox-parent
{
    width: 100%;
    height: 100%;

    display: flex;
    flex-direction: column;
    
    justify-content: flex-start; /* align items in Main Axis */
    align-items: stretch; /* align items in Cross Axis */
    align-content: stretch; /* Extra space in Cross Axis */
            
    background: rgba(255, 255, 255, .1);
}

.flexbox-item
{
    padding: 8px;
}
.flexbox-item-grow
{
    flex: 1; /* same as flex: 1 1 auto; */
}

.flexbox-item.header
{
    background: rgba(255, 0, 0, .1);
}
.flexbox-item.footer
{
    background: rgba(0, 255, 0, .1);
}
.flexbox-item.content
{
    background: rgba(0, 0, 255, .1);
}

.fill-area
{
    display: flex;
    flex-direction: row;
    
    justify-content: flex-start; /* align items in Main Axis */
    align-items: stretch; /* align items in Cross Axis */
    align-content: stretch; /* Extra space in Cross Axis */
    
}
.fill-area-content
{
    background: rgba(0, 0, 0, .3);
    border: 1px solid #000000;
    
    /* Needed for when the area gets squished too far and there is content that can't be displayed */
    overflow: auto; 
}
````

#2eme exemple (stretch)
##HTML
````
<div class="wrapper">
  <box1 class="box box1">
    <top class="top">top</top>
    <bottom class="bottom">
    Box 1. et wwerwer wer wer wer wer wer wer wer wer wer wer wer et wet wer wer wer wer we Box 1. et wwerwer wer wer wer wer wer wer wer wer wer wer wer et wet wer wer wer wer we
    Box 1. et wwerwer wer wer wer wer wer wer wer wer wer wer wer et wet wer wer wer wer we Box 1. et wwerwer wer wer wer wer wer wer wer wer wer wer wer et wet wer wer wer wer we   
    Box 1. et wwerwer wer wer wer wer wer wer wer wer wer wer wer et wet wer wer wer wer we Box 1. et wwerwer wer wer wer wer wer wer wer wer wer wer wer et wet wer wer wer wer we 
    Box 1. et wwerwer wer wer wer wer wer wer wer wer wer wer wer et wet wer wer wer wer we Box 1. et wwerwer wer wer wer wer wer wer wer wer wer wer wer et wet wer wer wer wer we      
    </bottom>
  </box1>
  <box2 class="box box2">
    <top class="top">top</top>
    <bottom class="bottom">
      Box 2
    </bottom>
  </box2>
  <box3 class="box box3">
    <top class="top">top</top>
    <bottom class="bottom"> 
    Box 3
   </bottom>
  </box3>
</div>
````

##CSS
````
.wrapper {
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  display: flex;  
  -webkit-flex-flow: row wrap;
  flex-flow: row wrap;
}

.wrapper > * {
  
}

.header {
  background: tomato;
}

.footer {
  background: lightgreen;
}

.box1 {
  background: deepskyblue;
}

.box2 {
  background: gold;
}

.box3 {
  background: hotpink;
}

 .box { 
  display:flex;
  margin:0 10px;
  flex: 1;
  flex-flow: column;
  align-content:stretch;
  align-items:stretch;
}

.top{
  flex:1;
  align-self:stretch;
}
.bottom{
  flex:2;
  background-color:blue;
  align-self:stretch;
}
````
