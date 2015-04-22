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

*aria-dropeffect
*aria-grabbed (state)

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
