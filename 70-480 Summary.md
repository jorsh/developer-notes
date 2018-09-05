# 70-480 Summary

## HTML

### Lesson 1: Introducing HTML5

- An element is composed of a starting tag, inner content, and an ending tag.
- Browsers ignore tags that are not recognized.
- HTML5 originates from HTML 4.01, not from XHTML.
- The W3C is responsible for developing open standards for the web.
- HTML elements provide structure, CSS style sheets provide presentation, and JavaScript provides behavior.
- Use lowercase tag names.
- Attribute values should always be quoted using either single quotes or double quotes.
- Boolean attributes are attributes whose mere presence on the starting tag indicates that the option is set.
- HTML5 defines global attributes, which are the set of attributes that can appear on any HTML5 element.
- Self-closing tags are tags whose beginning and ending tags are together to create an element with no content. Self-closing tags should be used only with elements that cannot have content.
- Void elements cannot have content. They should be created by using self-closing tags.
- Expando attributes are attributes that you define and are also known as author-defined attributes or custom attributes. Prefix these attributes with “data-“.
- You can use conditional comments to add a browser-specific source that will work with Internet Explorer but be treated as a comment by other browsers.
- HTML entities are special characters and can be embedded in your HTML document by using the ampersand (&), the entity name, and a semicolon (;). You can also use the ampersand (&), the hash symbol (#), the entity number, and the semicolon (;).
- Nonbreaking spaces can be used to render several contiguous spaces. You can also use nonbreaking spaces to keep two words from being separated by a line break.
- The id attribute specifies a unique identifier for an element.

### Lesson 2: Embedding content

- You can use the <iframe> element to provide reuse of HTML by embedding an HTML document in your current HTML document.
- Use the sandbox attribute on the <iframe> tag to help prevent malware and annoyances such as pop-ups from being introduced when the content is embedded in your HTML page.
- Use the seamless attribute on the <iframe> tag to indicate that the source content is to be rendered to appear as though it’s part of the containing document.
- The <a> tag creates a hyperlink to either an external HTML document or an internal location in the current document. The <a> tag can also be used to send email messages.
- The <img> element is a void element and is used to add an image reference to your HTML document.
- JPG is best for displaying photos on HTML pages due to its compression, GIF is best for small images with transparency and embedded animations, PNG is best for storage due to lossless compression during editing sessions, and SVG is best for drawings due to its vector drawing scalability.
- You can create a clickable image map by using the <map> and <area> elements.
- You can use the <embed> tag to provide simple content embedding.
- You can use the <object> tag to provide content embedding with greater flexibility because it can have nested <param> elements.

## CSS

### Lesson 1: Introducing CSS3

- A style rule, or style, is composed of two parts: the selector and the declaration block.
- The selector locates the elements in the HTML document to be styled.
- The declaration block contains the formatting instructions (declarations).
- Styles can be inline, embedded, or external.
- To maintain separation between structure and presentation, use external style sheets.
- Use the media attribute of the <link> element to specify the target device for a style sheet.

### Lesson 2: Understanding selectors, specificity, and cascading

- A style rule, or style, is composed of two parts: the selector and the declaration block. The selector locates the elements in the HTML document that will be styled. The declaration block contains the formatting instructions (declarations).
- Styles can be inline, embedded, or external.
- To maintain separation between structure and presentation, use external style sheets.
- Use the media attribute of the <link> element to specify the target device for a style sheet.
- Pseudo classes provide another way to select elements. Pseudo elements provide access to information that is not available from the DOM. Use two colons (::) to denote pseudo elements.
- Use the “!important” modifier with user-defined styles to override author-defined styles.
- Cascading precedence is by importance, specificity, and then textual order.
- The evaluation order of style sheets is the browser’s built-in style sheet, the user-defined style sheet, the author’s normal style sheet, the author’s important style sheet, and the user’s important style sheet.
- Calculating the specificity of a selector is based on three levels of magnitude.
- Element styles that are not assigned can inherit their style from a parent element.

### Lesson 3: Working with CSS properties

- CSS colors can be set using color names; hexadecimal notation; or the rgb, rgba, and hsl functions.
- Use the opacity property to set the transparency.
- To format text, set the font-family property and then set the font properties.
- Font families that have curls at the top and bottom of characters belong to the serif font family group. Font families that don’t have curls belong to the sans serif font family group. Font families whose characters are all the same width belong to the monospaced font family group. Font families that imitate handwriting belong to the cursive font family group. Font families that are decorative belong to the fantasy font family group.
- The CSS box model defines element content as surrounded by padding, which is then surrounded by the border, which is then surrounded by the margin.
- You can set all four sides of the margin, padding, and border by providing a single size to be applied to all sides, or you can set individual sides by adding -top, -bottom, -left, or -right to the property and assigning a value to each.
- The <div> element can be positioned by assigning a value of static, relative, absolute, or fixed to the position property.
- The float property can be used to create columns without removing the <div> element from HTML flow. This property can also be used to position images so that text flows around the image.
- Use the clear property to indicate when an element is to be positioned clear after the previous element.
- Use the box-sizing property to change the default width calculation from content to border.
