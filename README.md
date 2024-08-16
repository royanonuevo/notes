# CSS Precedence Guidlines


## Specificity hierarchy

1. Inline styles (Presence of style in document).
An inline style lives within your XHTML document. It is attached directly to the element to be styled. E.g.

2. IDs (# of ID selectors)
ID is an identifier for your page elements, such as #div.

3. Classes, attributes and pseudo-classes (# of class selectors).
This group includes .classes, [attributes] and pseudo-classes such as :hover, :focus etc.

4. Elements and pseudo-elements (# of Element (type) selectors).
Including for instance :before and :after.

## CSS Precedence Pattern
( 0, 0, 0, 0 ) => (inline style, id, classes/attributes/pseudo classes, element/pseudo elements)


## Examples
<pre>
div p.bio {font-size: 14px}       // ( 0, 0, 1, 2 )
#sidebar p {font-size: 12px}      // ( 0, 1, 0, 1 )
body #content .data img:hover     // ( 0, 1, 2, 2 )
ul#nav li.active a                // ( 0, 1, 1, 3 ) 
body.ie7 .col_3 h2 - h2           // ( 0, 0, 2, 3 )
#footer *:not(nav) li             // ( 0, 1, 0, 2 )
h1 style="color: red"             // ( 1, 0, 0, 0 )
ul > li ul li ol li:first-letter  // ( 0, 0, 0, 7 )
</pre>
