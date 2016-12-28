#ARIA Text-Resize Detection
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

