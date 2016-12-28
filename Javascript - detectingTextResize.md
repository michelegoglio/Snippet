#Text-Resize Detection
When you design for the web, you don’t know what software people will use to experience your site, and you don’t know what capabilities your users (and their software) have. Flexible layouts and resizable type can eliminate a lot of worst-case usability and design scenarios, but it’s still extremely difficult to create page layouts that don’t break even if the user increases the type size by more than a few settings.

##How to detect font size changes
It is remarkably easy to detect changes in font size. All you need is JavaScript that

* creates a hidden span element with a space inside it,
* reads the height of that element and stores it,
* registers listener functions to call when the font size changes, and
* checks periodically if the height of the span element changed—which means that the user has resized the font.

This is nothing new, and it has been used on some high-traffic web portals before. It becomes a lot more interesting, though, when you mix it with custom events. In essence, using a custom event means you get notified every time there is a change in font size.

Check the demo page to see the effect in action. (Resize the font in your browser to get the notifications.)

##Using the text resize detector
To implement this script, first embed it in the head of your document. (Line wraps marked » —Ed.)

````
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" »
"http://www.w3.org/TR/html4/strict.dtd">
<html dir="ltr">
<head>
  <meta http-equiv="Content-Type" content="text/html; »
charset=utf-8"> 
  <title>Font Resizer Demo</title>
  <script type="text/javascript" src=" »
textresizedetector.js"></script>
</head>
<body>
  <h1>Resize me, now!</h1>
</body>
</html>
````
Next, define two properties:

* The id of the element you want to add the span to and
* the name of the function that gets called when the text resize detector is initialized.

These are stored in two parameters called TARGET_ELEMENT_ID and USER_INIT_FUNC respectively.

````
  <script type="text/javascript" »src="textresizedetector.js"></script>
  <script type="text/javascript">
    // <![CDATA[
    /* id of element to check for 
       and insert test SPAN into */
    TextResizeDetector.TARGET_ELEMENT_ID = 'header';
    /* function to call once TextResizeDetector
       was initialized */
    TextResizeDetector.USER_INIT_FUNC = init;
    // ]]>
  </script>
````

Note: to determine the correct base font of the document, the element with the id that you store in TARGET_ELEMENT_ID should be fairly high in the source order and not inherit font size from any other element. This also means that the detector runs as soon as possible.

If you don’t care about the base font size, you can specify any element.

Lastly, define the function that you set in the USER_INIT_FUNC property.

````
  <script type="text/javascript" »
src="textresizedetector.js"></script>
  <script type="text/javascript">
    // <![CDATA[
    function init(){
      var iBase = TextResizeDetector.addEventListener( »
onFontResize,null );
      alert( "The base font size = " + iBase );
    }
    // id of element to check for and insert control
    TextResizeDetector.TARGET_ELEMENT_ID = 'header';
    /* function to call once TextResizeDetector
       was initialized */
    TextResizeDetector.USER_INIT_FUNC = init;
    // ]]>
</script>
````

The init() function is where you register listeners with addEventListener. This ensures that your function—in this caseonFontResize()—is called when the font size has been changed. It also returns the base font size, which is useful for Opera and IE7 users.

##A TANGENT: OPERA AND IE7
These browsers take a different approach to resizing: instead of increasing the font size, they zoom the whole document, including form elements and images. As these browsers don’t resize the font, the event will never fire. However, the script allows you to initially read out the base font size and help you adjust your layout / widget according to that base size.

##BACK TO WORK
Once you’ve set everything up, you can define your listener function. (Line wraps marked » —Ed.)

````
  <script type="text/javascript" »
src="textresizedetector.js"></script>
  <script type="text/javascript">
    // <![CDATA[
    function init(){
       var iBase = TextResizeDetector.addEventListener( »
onFontResize,null );
      alert( "The base font size = " + iBase );
    }
    function onFontResize( e, args ){
      var msg = "\nThe base font size in pixels: " + »
args[0].iBase;
      msg +="\nThe current font size in pixels: " + »
args[0].iSize;
      msg += "\nThe change in pixels from the last  »
size:" + args[0].iDelta;
      alert( msg );
    }
    // id of element to check for and insert control
    TextResizeDetector.TARGET_ELEMENT_ID = 'header';
    // function to call once TextResizeDetector has init'd
    TextResizeDetector.USER_INIT_FUNC = init;
    // ]]>
  </script>
````

When the event fires, this function retrieves two parameters: the name of the event—textSizeChanged—and an array of arguments, the first of which is an object with the following properties:

`iBase`
The initial value of the document when it was loaded.

`iDelta`
The difference between the last font size and the new font size.

`iSize`
The new font size.
All font sizes are in pixels.

The `TextResizeDetector` object itself has three methods:

`addEventListener()`
Registers your event handler and returns the base font size. If you pass an object as a second parameter, your handler function is executed in the scope of that object.

`stopDetector()`
Stops the detector.

`startDetector()`
Starts the detector. This is only needed if the stopDetector() method has been executed beforehand.

##Possible Uses
That’s grand, but what do you do with this information? Whatever you please. Possible options include
* Turning a horizontal menu bar into a vertical single list when the font is too large.
* Replacing a graphical button with a normal submit on large fonts
* Applying different style sheets to the document according to font size. You could also automatically switch to a zoom layout at a certain stage.
* Removing elements when a certain size is reached.
* Showing more elements when a certain size is reached (in case the user zooms out instead of in).
* Pulling in longer text passages via Ajax when the screen space allows for longer texts.
* Increase the width of a sidebar when the font size changes to keep a consistent line length.
* Center an element that is defined in em on the screen.

How else might this script be used? Tell us about it in the comments.
