#developing web components

##Chapter 1. Introduction

Jarrod Overson and Jason Strimpel

Oh, good, you’re here! Welcome! We hope you’re in for a fun ride. If you’re the type of person who skips the prefaces 
of books, we need to go over something real quick: this book is set up in a way that takes you through basic widget 
creation from a jQuery background and then translates that knowledge and understanding first into the world of web 
components, and then into that of Polymerized web components (web components created using the Polymer framework).

Web components are on the bleeding edge, barely supported in the most modern of modern browsers, and we have a fair 
way to go before people start falling into generally accepted best practices. The Polymer group is leading the way, 
with Mozilla having its own spin, and individuals in the community are adding in their own opinions as web components 
start being adopted in real-world applications.

In this environment, we felt that the greatest tool that we could put in the hands of developers interested in web 
components was an understanding of how to develop facets of the user interface (UI) in a reusable manner that can also 
translate directly to web components if (and when) you decide to use them.

In this book we’ll be tackling the UI aspects for a common JavaScript widget, the dialog box. We’ll go from basic 
creation to a vanilla web component, and then look at using Polymer to abstract it, build it, and deploy it as a 
reusable custom HTML element.

One of the biggest takeaways we want you to have after reading this book is that the introduction of web components, 
while it changes so much, doesn’t remove the need to know and understand how to write modern JavaScript, and it doesn’t 
invalidate the plethora of libraries and practices we’ve come to rely on and appreciate as part of frontend web 
development. With that said, web components certainly are a fresh and exciting way of tackling encapsulated logic 
and user interfaces and the landscape is full of innovation and opportunity.

*CHOOSE YOUR OWN ADVENTURE*
This book is broken into four parts, allowing you to begin reading about the particular subject that most interests you. Are you already familiar with the concepts in Part I, UI Core Concepts? Then skip ahead to Part II, Building Our UI. Not interested in learning UI component implementation details and how to construct a dialog component? Then dive right into Part III, Building HTML5 Web Components, and learn all about this new technology. Already know about web components and are itching to learn how to use them in production applications? Then Part IV, Testing, Building, and Deploying Components with Polymer is for you. Where you begin and end is entirely up to you, and we wish you success on your adventure!

###What Are Web Components?
“Web components” aren’t any one thing; this is the term used for a collection of technologies that enable developers to 
effectively describe the implementations of HTML elements that already exist.

What does that even mean?

Well, if given the task of implementing a <p> tag via some other combination of HTML, JavaScript, and CSS, 
how would you do it? You could reasonably assume that the <p> tag just describes a set of styles and then maybe 
write a <div> with some inline style, or maybe a p class that groups paragraph styles together.

Now how would you implement, say, a <select> tag and its constituent list of <option> tags? That starts to get 
more complicated. It’s doable, sure, but it’s going to start being a hairy mess of styles, JavaScript, and HTML. 
Then consider how fragile the implementation would be. The styles may collide with the using page, as may classes, 
IDs, global JavaScript, etc. Again, it’s doable, and we have done it, but it’s far from ideal.

Further down that same path, how would you implement the <video> tag? This starts getting dicier and dicier, and 
these are the types of problems that web components technologies seek to solve. They don’t go all the way, but they 
give developers a standard way to encapsulate, protect, and package these concepts.

Even if you don’t think web components are the bee’s knees (which they are, to the extent to which a bee’s knees 
could possibly make web development a lot more satisfying and exciting), the constituent technologies are all 
independently useful and will undoubtedly find their way into frameworks like Angular and Ember, so they are worth 
being aware of and understanding.

What’s intriguing about web components is that the bulk of it is maddeningly obvious. Two years after you buy into 
web components whole hog, you will look back at the twenty-aughts as this primitive time filled with Neanderlithic 
frameworks and “best practices” that involved putting whole string templates in `<script>` tags. When recalling this 
era of development to your grandchildren, they will look at you with skepticism and ask disbelievingly, “Gramps, 
did you really not have native templates in your DOM or are you just yanking our chains?”

And you’ll say: “It’s true, sweet Becca and little Johnny—now go play with your robots and don’t touch my space 
bike.”

Following is a rundown of some of the key areas we’ll be exploring in this book.

####HTML Templates
HTML templates are the simple embodiment of a templatized, inert Document Object Model (DOM) that can be stamped out 
and reused over and over again. Before the <template> tag, there existed any number of ways that you could reuse HTML. 
You could write your own functions that created and populated DOM nodes directly via DOM methods, you could retrieve 
text stored in the DOM via innerHTML and run that through a template engine, you could “precompile” templates in the 
build phase and send template functions, or you could choose some other equally uncomfortable method.

Now it’s all over. There is one way to write reusable HTML. Its usage can certainly differ, but one thing’s for sure: 
you’re going to be writing your templates and partials in <template> tags from now on.

####HTML Imports
The HTML import is another foolishly simple concept that accommodates a single interaction point for 
independent bundles to be loaded by. What has already been done for <script> and <style> tags has now been 
done for HTML itself. The bonus, on top of what was done for scripts and styles, is that the imported HTML 
can then infinitely link to all its own dependencies in the same formats that already exist. This will allow 
a developer to include miniature applications and all their dependencies with a single @include, instead of 
tracking everything down and including all the sources or links directly.

####Custom Elements
Finally! There now exists a standard way of generating custom elements across framework, platform, and all 
other boundaries. The core of HTML, the single element, is now open to everyone. The custom element API is 
incredibly trivial, and it’s meant to be. This is the first step to building HTML into what our apps have always
wanted to be. This is about far more than simply creating new textual tags; it’s opening up a strict API touchpoint 
that everyone is inherently familiar with. It’s a contract that is already agreed upon, tolerated, and enjoyed by every 
web developer that exists.

####The Shadow DOM
The shadow DOM is the secret sauce to web components. Each other technology on its own provides value that 
is obvious and appreciated, but the shadow DOM is the icing on the web component waffle. It finally provides a
way for us to isolate portions of the DOM for true protection from styling, access, and modification via common 
means. For anyone who has ever tried to build reusable UIs, this is a welcome change that could nearly bring a tear
to the eye of the most jaded developer.

Combining each of these things, we have the ability to generate custom elements, generating their own subtrees 
that are isolated from the parent DOM, all importable via a single tag!

If we sound excited, it’s because development with web components is like breathing fresh air after being in a 
coal mine for two decades. Like standing up after 50 pounds of weight have been removed from your back. It’s a 
freedom that is welcome and genuinely exciting.

###Why Web Components?
The Web is in a transitional state, and has been for quite some time. It was originally designed to view documents—that’s 
why the applications we use to sift through its contents are called browsers! Since its inception, though, the Web has 
been slowly morphing into an application platform, radically transforming the software development landscape. It has 
never been easier to release a new version of an application: a developer pushes code changes or new assets to a server, 
and the end user refreshes the page (as someone once said, a page refresh is the “compile” of web development). 
Unfortunately, the browser has not kept pace with this revolution, forcing developers to come up with clever solutions 
to make the Web more of an application platform.

The past few years have seen the emergence of JavaScript Model-View-Controller (MVC) libraries and frameworks 
designed to help give web applications structure.

*NOTE*
The JavaScript MVC libraries that have been released over the past few years have not all been strictly MVC. 
The acronym MV* was created to encompass other patterns, such as MVVM and MVP.

Module loaders such as Require.JS have also helped greatly, providing more structure by supplying the equivalent 
(and more) of the missing import that is standard in other platforms. This has allowed frontend engineers to think 
more modularly. Before the rise of MVC, we saw the rise of jQuery and UI widget libraries. These libraries were 
developed to help normalize web development as much as possible and to fill in the gaps in the limited set of UI 
components available on the Web. Before these libraries, writing JavaScript that interacted with the DOM across 
browsers was a nightmare and simple forms were the only UI natively supported by the browsers.

If you step back and look objectively at the current state of web development, it is really a giant hack—but 
that has been changing in recent years.

*NOTE*
The fact that it is a hack, in a sense, is not altogether bad. It has provided a sense of freedom that 
other platforms and languages lack. Irritating as it can be at times, it’s hard to imagine developing in a 
more restrictive environment.

The emergence of HTML5 and newer APIs is evidence of a great attempt at turning the Web into a real application 
platform. However, it is still missing some important features that are in most other application platforms.

For instance, the Web is not extensible. You cannot create new types of elements or extend existing ones, and 
there are no imports or methods for encapsulating components. Enter web components.

The term “web components” is currently being thrown around in the same way as “HTML5.” Both terms have different 
meanings for different people. Taken literally, HTML5 is simply a new document type with more elements. However, 
when people talk about HTML5 they are typically including the new elements, CSS3, and the new JavaScript APIs, 
which together redefine web development. The same is true of web components—the term is used to reference a new 
collection of features that, when utilized together, allow developers to create reusable components in a standard 
fashion.

Imagine a world in which the web platform is natively extensible. Any element can be extended, and new elements 
can be defined to easily create rich user interfaces. Also, imagine a world in which these extensions can be imported 
in a uniform fashion, including all assets such as JavaScript, CSS, and images. Imagine that this system has been 
optimized to deduplicate requests for the same import and that blocks of markup can be loaded and marked as inert 
so as not to impact performance. Imagine a real application platform, if you will. This is the promise of web 
components.

What if you could create a dialog component simply by importing the resource and declaring meaningful markup?

````
<head>
    <link rel="import" href="/imports/dialog/index.html">
</head>
<body>
    <dialog-component title="After Ford">
        Ending is better than mending. <br />
        The more stitches, the less riches.
    </dialog-component>
</body>
````
That would be a huge improvement in terms of readability over the current standard:
````
<!-- based on http://jqueryui.com/dialog/ -->
<head>
    <link
     rel="stylesheet"
     href="//code.jquery.com/ui/1.11.0/themes/smoothness/jquery-ui.css">
    <script src="//code.jquery.com/jquery-1.10.2.js"></script>
    <script src="//code.jquery.com/ui/1.11.0/jquery-ui.js"></script>
    <script>
        $(function () {
            $( "#dialog" ).dialog();
        });
    </script>
</head>
<body>
    <div id="dialog" title="After Ford">
        Ending is better than mending. <br />
        The more stitches, the less riches.
    </div>
</body>
````
This is not to say that current widget libraries do not have anything to offer or that their patterns are flawed. 
In fact, they are still quite relevant given the current browser support for web components. Additionally, the web 
components specification alone is not a panacea for creating rich user interfaces. A dialog component would still be 
driven by the same code as a dialog widget. However, the dialog component would wrap the widget code in a simplified, 
standardized, native interface with a convenient method for including its dependencies.

While this might not sound like a vast improvement, the ability to extend, abstract, import, and encapsulate natively 
will make the development of web applications much easier. It will allow developers to create reusable elements with 
standard life cycles that can be imported by any application. This standardization will form an implicit contract 
between the elements and the application, making the creation and management of interfaces a much smoother process.
