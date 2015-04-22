#ARIA Landmarks
ARIA land mark roles helps in bridging this gap. ARIA landmarks provide systematic way of conveying the various divisions of the web page to the users of screen readers. In this post we will understand how the screen readers handle land mark roles.

* Banner
* Navigation
* Search
* Main
* Form
* Contentinfo
* Complementary




##Banner
A region that contains the prime heading or internal title of a page.

````
<div role=”banner>
</div>
````

Screen Reader support
JAWS recognizes the beginning and end of the banner region and announces “Banner Region Start” and “Banner Region end.
NVDA 2012.3 recognizes the beginning of the banner region but could not announce when it ends. NVDA announces “Banner Region start” at the beginning of the banner land mark.
VoiceOver on IOS recognizes banner land mark but it announces “land mark start” and “Land mark end”. It does not say which land mark it is.
Talkback on Android says just “Banner” at the beginning of the land mark. It does not identify the end of the land mark.
Navigation
A collection of links suitable for use when navigating the document or related documents.

Syntax:
<div role=”navigation”>
</div>

Screen reader support
JAWS recognizes the beginning and end of the navigation region and announces “Navigation Region Start” and “Navigation Region end.
NVDA 2012.3 recognizes the beginning of the Navigation region but could not announce when it ends. NVDA announces “Navigation landmark” at the beginning of the Navigation land mark.
VoiceOver on IOS recognizes Navigation land mark but it announces “land mark start” and “Land mark end”. It does not say which land mark it is.
Talkback on Android says just “Navigation” at the beginning of the land mark. It does not identify the end of the land mark.
Search
The search tool of a Web document.

Syntax:
<div role=”search”>
</div>

Screen Reader support
JAWS recognizes the beginning and end of the search region and announces “Search Region Start” and “Search Region end.
NVDA 2012.3 recognizes the beginning of the Search region but could not announce when it ends. NVDA announces “Search Region start” at the beginning of the search land mark.
VoiceOver on IOS recognizes search land mark but it announces “land mark start” and “Land mark end”. It does not say which land mark it is.
Talkback on Android says just “search” at the beginning of the land mark. It does not identify the end of the land mark.
Main
Main content in a document.

<div role=”main”>
</div>

Screen Reader Support
JAWS recognizes the beginning and end of the main region and announces “Main Region Start” and “Main Region end.
NVDA 2012.3 recognizes the beginning of the Main region but could not announce when it ends. NVDA announces “Main landmark” at the beginning of the Main land mark.
VoiceOver on IOS recognizes Main land mark but it announces “land mark start” and “Land mark end”. It does not say which land mark it is.
Talkback on Android says just “Main” at the beginning of the land mark. It does not identify the end of the land mark.
Content info
Meta information which applies to the first immediate ancestor whose role is not presentation.

<div role=”contentinfo”>
</div>

Screen Reader support
JAWS recognizes the beginning and end of the Contentinfo region and announces “Contentinfo Region Start” and “Content info Region end.
NVDA 2012.3 recognizes the beginning of the Content info region but could not announce when it ends. NVDA announces “Content info landmark” at the beginning of the Content info land mark.
VoiceOver on IOS recognizes Content info land mark but it announces “land mark start” and “Land mark end”. It does not say which land mark it is.
Talkback on Android says just “Content info” at the beginning of the land mark. It does not identify the end of the land mark.
Complementary
Any section of the document that supports but is separable from the main content, but is meaningful on its own even when separated from it.

Syntax:
<div role=”complementary”>
</div>

Screen Reader Support
JAWS recognizes the beginning and end of the Complementary region and announces “Complementary Region Start” and “Complementary Region end.
NVDA 2012.3 recognizes the beginning of the Complementary region but could not announce when it ends. NVDA announces “Complementary landmark” at the beginning of the Content info land mark.
VoiceOver on IOS recognizes Complementary land mark but it announces “land mark start” and “Land mark end”. It does not say which land mark it is.
Talkback on Android says just “Complementary” at the beginning of the land mark. It does not identify the end of the land mark.

Form
A region of the document that represents a collection of form-associated elements, some of which can represent editable values that can be submitted to a server for processing.

<div role=”form”>
</div>

Screen Reader Support
JAWS recognizes the beginning and end of the Form region and announces “Form Region Start” and “Form Region end.
NVDA 2012.3 do not recognize the Form region.
VoiceOver on IOS do not recognize Form land mark.
Talkback on Android says just “Form” at the beginning of the land mark. It does not identify the end of the land mark.
Other Notes:
Use JAWS short-cut key “;” (semi column) to jump from one landmark to another landmark on the web.
Use NVDA short-cut key “d” to jump from one landmark to another landmark on the web page.
NVDA provides the landmarks list from “Elements list” which can be pulled out by using short-cut insert + f7.
VoiceOver on IOS provides landmarks under the rotor elements.
JAWS does not recognize Form land mark on Google Chrome.
