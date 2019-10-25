# px, em, rem?

Use <code>em</code> only for sizing that needs to scale based on the font size of an element other than the html (root) element.

Use <code>rem</code> unit for elements that scale depending on a user's browser font size settings. Use <code>rem</code> as the unit for most of your property value.

For complex layout arrangement, use percentage (<code>%</code>).

User can change the font-size within the browser setting (difficult to find). This has no effect if <code>px</code> are used (main reason to discard <code>px</code>?)

* Pixels are ignorant, don’t use them. ?
* Use <code>rem</code> for sizes and spacing.
* <code>rem</code> and <code>em</code> units are computed into pixel values by the browser, based on font sizes in your design.
* <code>em</code> units are based on the font size of the element they’re used on.
* <code>rem</code> units are based on the font size of the html element.
* <code>em</code> units can be influenced by font size inheritance from any parent element
* <code>rem</code> units can be influenced by font size inheritance from browser font settings.
* Use <code>em</code> units for sizing that should scale depending on the font size of an element other than the root.
* Use <code>rem</code> units for sizing that doesn’t need <code>em</code> units, and that should scale depending on browser font size settings.
* Use <code>rem</code> units unless you’re sure you need <code>em</code> units, including on font sizes.
* Use <code>rem</code>? <code>em</code>? units on media queries. Found both as best practices (<code>em</code> seems also to work with safari)
* Don’t use <code>em</code> or <code>rem</code> in multi column layout widths - use % instead.
* Don’t use <code>em</code> or <code>rem</code> if scaling would unavoidably cause a layout element to break.

## Tip
When creating layouts it’s often easier to think in pixels but output in <code>rem</code> units.

You can have pixel to <code>rem</code> calculations done automatically via a preprocessor like Stylus / Sass / Less, or a postprocessor like PostCSS with the PXtoRem plugin.

Use <code>%</code> for font-size