Microformats2
Classic microformats have been serving the web community’s need to extend HTML’s expressive power since 2004. Through an evolutionary, open, rigorous community process and human-first design principles, structured use of the class and rel attributes have paved the cowpaths of publishing data about people, places, events, reviews, products and more.
Microformats2 is the next big effort by the community to improve how microformats are authored, parsed and defined. Version two has multiple working open source implementations which independents are using in production and is easier to publish and consume than ever.
In this series of guides I’ll show you how to be the next site publishing and consuming microformats.
You can see how a microformats parser sees your markup by pasting any of the code samples below into this php-mf2 sandbox. Go ahead and experiment with adding more properties and see what happens!















Incremental Steps
In order to demonstrate some of the differences between microformats 2 and Classic Microformats/other competing technologies, I’ll use the process of content-out markup — going from plain text to HTML and finally adding a sprinkling of microformats. Let’s start with my favourite example: mentioning a person.
As plain text:
Barnaby Walters 
With HTML:
<a href="http://waterpigs.co.uk">Barnaby Walters</a> 
With classic microformats:
<span class="vcard"><a class="fn n url" href="http://waterpigs.co.uk">Barnaby Walters</a></span>

That’s 37 extra characters and a whole extra nested element just to say “This link is to a person”, not to mention the strangely named root classname (vcard? I thought this was an hcard?) and multiple crypticfn n classnames. Competing technologies are typically even longer and messier.
With microformats 2 this all becomes much simpler:
<a class="h-card" href="http://waterpigs.co.uk">Barnaby Walters</a> 

Weighing in at only 15 characters, this is quicker to type, easier on the eyes and easier to remember.
There are two fundamental changes in microformats 2 which make this helium-esque lightness possible: Implied Properties and prefixed classnames.









Implied Properties
When you give class=h-card to an element, you’re saying “This element represents a person”. In many cases the element will be simple; just a name, perhaps with a link or photo. Why should you add extra elements and classnames just to tell a dumb computer which bit is the name, URL or photo URL when that information is already expressed by the markup?
Implied properties save you from this tedium. When you specify an element as an h-card without explicitly defining which parts are the name, url or photo url, the parser will figure out what you meant. And it’s not just for h-cards either — thanks to the new generic parsing in microformats 2, this shorthand works for any microformat.


















Prefixed Classnames
Classic microformats used plain classnames which looked like any other (e.g. vcard, n or note). There were a few problems with this — classnames would clash, cause false positives or be thrown away by developers who weren’t microformats-aware (“these classnames aren’t doing anything!”).
This also meant parsers were tricky to write, as each one had to maintain a long list of classnames used by each microformats, resulting in many parsers quickly going out of date.
Prefixing classnames solves both of these problems: semantic microformats2 classnames are set apart from styling hooks, and parsers can figure out which classnames to look for, cutting down on maintenance. There are 5 prefixes:
•	h-* root classnames specify that an element is a microformat, e.g. <span class="h-card">
•	p-* specifies an element as a plain-text property, e.g. <span class="p-name">My Name</span>
•	u-* parses an element as a URL, e.g. <a class="u-url" href="/"></a>
•	dt-* parses an element as a date/time, e.g. <time class="dt-published" datetime="2013-05-02 12:00:00" />
•	e-* parses an element’s whole inner HTML, e.g. <div class="e-content">

I’ll demonstrate the use of all of these prefixes with some real-world examples.
Firstly, another h-card, more fleshed out than the earlier example. This might be the sort that you put on your homepage:
<div class="h-card">
  <p><img class="u-photo" href="/me.png" alt="" /></p>
  <p class="p-name">
    <a href="u-url" href="http://waterpigs.co.uk">Barnaby Walters</a>
  </p>
</div>

p-name, u-url and u-photo are fairly standard properties you’ll see over and over again. Another improvement in microformats 2 is increasing consistency between different microformat specifications — again, making them easier to authors to remember and consumers to understand. A nice side effect is that a single element can be more than one type of microformat at once — for example a h-entry and h-review.
To demonstrate dt-* and e-*, here’s a note (like a tweet or short blog post), marked up using h-entry:
<article class="h-entry">
  <div class="e-content p-summary p-name">
    <p>Just writing a guide to using <a href="http://microformats.org/wiki/microformats-2">
microformats-2</a></p>
  </div>
  <time class="dt-published" datetime="2013-05-01 12:00:00">20 minutes ago</time> 
</article> 

Here, I want the HTML inside the content to be passed to the parser, so I mark it up as e-*. Notice I’m also specifying that content as the summary and name — one element can be parsed as multiple properties.
I’m using the time element to mark up the time this note was published. Because I’ve prefixed the classname with dt- and it’s on atime element, parsers know to look in the datetime attribute if it exists.















Combining Microformats
The third area in which microformats2 improves on the previous version is in combining microformats and making each microformat specification more reusable — for example, both a person or an event might have an address, so it makes sense to reuse the same markup for both.
There are many reasons to combine microformats — say you want to specify the author of a blog post or review. You would do so by making the p-author of the post an h-card:
<article class="h-entry">
  <p class="p-author h-card">Barnaby Walters</p>
  <p class="p-content">Blah blah blah</p>
  … 
Or a comment on an article, via h-cites as p-comments:

  …
  <article class="p-comment h-cite">
    <p class="p-author h-card">Jón Jónsson</p>
    <p class="p-summary">Woah that’s insightful.</p>
    <p><a class="u-url" href="http://jonsson.com/replies/1">
      <time class="dt-published" datetime="2014-03-01T14:00:25+00:00>
        2014-03-01 14:00
      </time>
    </a></p>
  </article>
</article> 

The reason comments are h-cites instead of h-entrys is that h-entry implies syndication — it’s something you’ve posted, or have re-posted, whereas a comment is a reference to a post on another site.
Or the address of a person or event, using h-adr:
<div class="h-event">
  <h1 class="p-name">Microformats Meetup</h1>
  <p>Join us at <b class="p-adr h-adr">
    <span class="p-street-address">Some Bar</span>,
    <span class="p-locality">Someplace</span></b>
  </p>
</div> 

