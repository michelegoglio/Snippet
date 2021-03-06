http://oaa-accessibility.org/examples/
#ARIA state and property

##Global States and Properties
Some states and properties are applicable to all host language elements regardless of whether a role is applied. The following global states and properties are supported by all roles and by all base markup elements.

* aria-atomic
* aria-busy (state)
* aria-controls
* aria-describedby
* aria-disabled (state)
* aria-dropeffect
* aria-flowto
* aria-grabbed (state)
* aria-haspopup
* aria-hidden (state)
* aria-invalid (state)
* aria-label
* aria-labelledby
* aria-live
* aria-owns
* aria-relevant

##Taxonomy of WAI-ARIA States and Properties
###Widget Attributes

This section contains attributes specific to common user interface elements found on GUI systems or in rich internet applications which receive user input and process user actions. These attributes are used to support the [widget roles](http://www.w3.org/TR/wai-aria/roles#widget_roles).

* aria-autocomplete
* aria-checked (state)
* aria-disabled (state)
* aria-expanded (state)
* aria-haspopup
* aria-hidden (state)
* aria-invalid (state)
* aria-label
* aria-level
* aria-multiline
* aria-multiselectable
* aria-orientation
* aria-pressed (state)
* aria-readonly
* aria-required
* aria-selected (state)
* aria-sort
* aria-valuemax
* aria-valuemin
* aria-valuenow
* aria-valuetext
 
Widget attributes might be mapped by a user agent to platform accessibility API states, for access by assistive technologies, or they might be accessed directly from the DOM. User agents MUST provide a way for assistive technologies to be notified when states change, either through DOM attribute change events or platform accessibility API events.

###Live Region Attributes

This section contains attributes specific to live regions in rich internet applications. These attributes may be applied to any element. The purpose of these attributes is to indicate that content changes may occur without the element having focus, and to provide assistive technologies with information on how to process those content updates. Some roles specify a default value for the aria-live attribute specific to that role. An example of a live region is a ticker section that lists updating stock quotes.

* aria-atomic
* aria-busy (state)
* aria-live
* aria-relevant



###Drag-and-Drop Attributes

This section lists attributes which indicate information about drag-and-drop interface elements, such as draggable elements and their drop targets. Drop target information will be rendered visually by the author and provided to assistive technologies through an alternate modality.

* aria-dropeffect
* aria-grabbed (state)

For more information about using drag-and-drop, see Drag-and-Drop Support in the WAI-ARIA Authoring Practices ([ARIA-PRACTICES]).

###Relationship Attributes

This section lists attributes that indicate relationships or associations between elements which cannot be readily determined from the document structure.

* aria-activedescendant
* aria-controls
* aria-describedby
* aria-flowto
* aria-labelledby
* aria-owns
* aria-posinset
* aria-setsize


##Definitions of States and Properties (all aria-* attributes)

Below is an alphabetical list of WAI-ARIA states and properties to be used by rich internet application authors. A detailed definition of each WAI-ARIA state and property follows this compact list.

* `aria-activedescendant`
Identifies the currently active descendant of a composite widget. Used to deal with multiple focusable children, ie. in a tree menu
````
<div role="toolbar" tabindex="0" aria-activedescendant="button1">
<img src="buttoncut.png" alt="cut" role="button" id="button1">
<img src="buttoncopy.png" alt="copy" role="button" id="button2">
<img src="buttonpaste.png" alt="paste" role="button" id="button3">
</div> 
````

* `aria-atomic`
Indicates whether assistive technologies will present all, or only parts of, the changed region based on the change notifications defined by the aria-relevant attribute. 
The `aria-atomic` property is an optional property that can have the values `true` or `false` (default). When the region is updated, the atomic property is used to indicate if assistive technologies should present all or part of the changed region to the user, and is influenced by the aria-relevant property. If the `aria-atomic` property is set to `true`, assistive technologies should present the entire region as a whole depending on the `aria-relevant` property; otherwise, the part of the region that changed might be announced on its own.

Sometimes, updates make sense on their own, such as a new line arriving in a chat application. Other times, changes in the content may not make sense without the context of other parts of the region. In these cases, `aria-atomic="true"` should be set on the relevant container so the region is presented as a whole. In the following example, if a change is made anywhere in the div element, the whole content is announced to the user.
````
<div aria-live="polite" 
    aria-atomic="true">
  <h3>Currently playing</h3>
  <p>Jake Bugg - Lightening Bolt</p>
</div>
````

* `aria-autocomplete`
Indicates whether user input completion suggestions are provided.
An `aria-autocomplete` property is used when the suggestions of user input items are known. The values of the `aria-autocomplete` can be none, inline, list or both.

`aria-autocomplete=”none”`: Default.
`aria-autocomplete=”inline”`: When the options are available and the user can type few characters in the text field and retrieve the appropriate options.
`aria-autocomplete=”list”`: Unlike the “inline” property user can only select an option from the list but will not be able to type in the text field.
`aria-autocomplete=”both”`: Combination of inline and list.
To intimate the user that the text fields are not just text fields use `aria-haspopup=”true”`. `Role=”combobox”` can also be used to provide an essence of a list items available along with the text field. Provide `aria-readonly=”true”` when author does not want the user to type in text field and only pick the option from the list available. It is used when the text field have `aria-autocomplete=”list”`. For `aria-autocomplete=”inline”`, `aria-autocomplete=”both”` and of course for `aria-autocomplete=”none”` aria-readonly should not be used or should be `aria-readonly=”false”`.
`aria-autocomplete` property has good support with JAWS 14 on Internet explorer 9, latest browsers of Google Chrome and Firefox. With NVDA 2013.3 Google Chrome has good support while remaining two browsers have partial support.
````
  <input aria-autocomplete="list" aria-controls="autocomplelist">
  <ul role="listbox" id="autocompletelist" aria-activedescendant="option1">
    <li role="listitem" id="option1">first option</li>
    <li role="listitem" id="option2">second option</li> 
  </ul>
````

* `aria-busy` (state)
Indicates whether an element, and its subtree, are currently being updated.
`ARIA-busy` state should be used by the content authors when a portion on a web page has auto updating content. `ARIA-busy` is a state having two possible values `ARIA-busy=”true”` and `ARIA-busy=”false”`.

`ARIA-busy=”true”` is set when a relevant portion of the page is currently getting updated and the users are waiting to read the updated content. Users of assistive technology will not be able to read anything while the content is getting updated. They could probably hear “busy” with few screen readers. Once the content is updated content authors can set `ARIA-busy=”false”` or remove the `ARIA-busy` attribute Once the content is updated the assistive technologies gather the updated information and provide it to the user.

`ARIA-busy` state is used as part of a live region. To notify the live region `ARIA-live` property is used. `ARIA-live` have three possible values `ARIA-live=”off”`, `ARIA-live=”polite”` and `ARIA-live=”assertive”`.

````
<h2>Current Score</h2> 
<p aria-live=”polite” aria-busy=”true”></p>
````
In the above example when the updation is done content authors should take care that the `ARIA-busy=”false”` and the updated content is available in the paragraph.


* `aria-checked` (state)
Indicates the current "checked" state of checkboxes, radio buttons, and other widgets. See related aria-pressed and aria-selected.

* `aria-controls`
Identifies the element (or elements) whose contents or presence are controlled by the current element. See related aria-owns.

* `aria-describedby`
Identifies the element (or elements) that describes the object. See related aria-labelledby.

* `aria-disabled (state)`
Indicates that the element is perceivable but disabled, so it is not editable or otherwise operable. See related `aria-hidden` and `aria-readonly`.

* `aria-dropeffect`
Indicates what functions can be performed when the dragged object is released on the drop target. This allows assistive technologies to convey the possible drag options available to users, including whether a pop-up menu of choices is provided by the application. Typically, drop effect functions can only be provided once an object has been grabbed for a drag operation as the drop effect functions available are dependent on the object being dragged.

* `aria-expanded (state)`
Indicates whether the element, or another grouping element it controls, is currently expanded or collapsed.

* `aria-flowto`
Identifies the next element (or elements) in an alternate reading order of content which, at the user's discretion, allows assistive technology to override the general default of reading in document source order.

* `aria-grabbed` (state)
Indicates an element's "grabbed" state in a drag-and-drop operation.

* `aria-haspopup`
Indicates that the element has a popup context menu or sub-level menu.

* `aria-hidden` (state)
Indicates that the element and all of its descendants are not visible or perceivable to any user as implemented by the author. See related `aria-disabled`.

* `aria-invalid` (state)
Indicates the entered value does not conform to the format expected by the application.

* `aria-label`
Defines a string value that labels the current element. See related `aria-labelledb`.

* `aria-labelledby`
Identifies the element (or elements) that labels the current element. See related `aria-label` and `aria-describedby`.

* `aria-level`
Defines the hierarchical level of an element within a structure.

* `aria-live`
Indicates that an element will be updated, and describes the types of updates the user agents, assistive technologies, and user can expect from the live region.

* `aria-multiline`
Indicates whether a text box accepts multiple lines of input or only a single line.

* `aria-multiselectable`
Indicates that the user may select more than one item from the current selectable descendants.

* `aria-orientation`
Indicates whether the element and orientation is horizontal or vertical.

* `aria-owns`
Identifies an element (or elements) in order to define a visual, functional, or contextual parent/child relationship between DOM elements where the DOM hierarchy cannot be used to represent the relationship. See related `aria-controls`.

* `aria-posinset`
Defines an element's number or position in the current set of listitems or treeitems. Not required if all elements in the set are present in the DOM. See related `aria-setsize`.

* `aria-pressed` (state)
Indicates the current "pressed" state of toggle buttons. See related aria-checked and `aria-selected`.

* `aria-readonly`
Indicates that the element is not editable, but is otherwise operable. See related `aria-disabled`.

* `aria-relevant`
Indicates what user agent change notifications (additions, removals, etc.) assistive technologies will receive within a live region. See related `aria-atomic`.

* `aria-required`
Indicates that user input is required on the element before a form may be submitted.

* `aria-selected` (state)
Indicates the current "selected" state of various widgets. See related aria-checked and `aria-pressed`.

* `aria-setsize`
Defines the number of items in the current set of listitems or treeitems. Not required if all elements in the set are present in the DOM. See related aria-posinset.

* `aria-sort`
Indicates if items in a table or grid are sorted in ascending or descending order.

* `aria-valuemax`
Defines the maximum allowed value for a range widget.

* `aria-valuemin`
Defines the minimum allowed value for a range widget.

* `aria-valuenow`
Defines the current value for a range widget. See related `aria-valuetext`.

* `aria-valuetext`
Defines the human readable text alternative of `aria-valuenow` for a range widget.
