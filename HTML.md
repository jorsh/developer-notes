# HTML

## Block versus inline elements

- Block-level elements form a visible block on a page — they will appear on a new line from whatever content went before it, and any content that goes after it will also appear on a new line.

  - Block-level elements tend to be structural elements on the page that represent.
  - **A block-level element wouldn't be nested inside an inline element, but it might be nested inside another block-level element.**
  - e.g.: paragraphs, lists, navigation menus, footers, etc.

- Inline elements are those that are contained within block-level elements and surround only small parts of the document’s content, not entire paragraphs and groupings of content.
  - An inline element will not cause a new line to appear in the document
  - e.g.: `<a>`, `<em>` or `<strong>`.

## Anatomy of a HTML document

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <p>This is my page</p>
  </body>
</html>
```

## Head and Metadata

- meta
- title
- script
- link

## Document and website structure

https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure

- **header**: `<header>`.
- **navigation bar**: `<nav>`.
- **main content**: `<main>`, with various content subsections represented by <article>, <section>, and `<div>` elements.
- **sidebar**: <aside>; often placed inside <main>.
- **footer**: <footer>.

## Layout Elements

- <main> is for content unique to this page. Use <main> only once per page, and put it directly inside <body>. Ideally this shouldn't be nested within other elements.
- <article> encloses a block of related content that makes sense on its own without the rest of the page (e.g. a single blog post.)
- <section> is similar to <article>, but it is more for grouping together a single part of the page that constitutes one single piece of functionality (e.g. a mini map, or a set of article headlines and summaries.) It's considered best practice to begin each section with a heading; also note that you can break <article>s up into different <section>s, or <section>s up into different <article>s, depending on the context.
- <aside> contains content that is not directly related to the main content but can provide additional information indirectly related to it (glossary entries, author biography, related links, etc.)
- <header> represents a group of introductory content. If it is a child of <body> it defines the global header of a webpage, but if it's a child of an <article> or <section> it defines a specific header for that section (try not to confuse this with titles and headings.)
- <nav> contains the main navigation functionality for the page. Secondary links, etc., would not go in the navigation.
- <footer> represents a group of end content for a page.

## Non-semantic wrappers

- <span> is an inline non-semantic element, which you should only use if you can't think of a better semantic text element to wrap your content, or don't want to add any specific meaning.
- <div> is a block level non-semantic element, which you should only use if you can't think of a better semantic block element to use, or don't want to add any specific meaning.

## Headings and Paragraphs

```html
<p>I am a paragraph, oh yes I am.</p>
<h1>I am the title of the story.</h1>
```

## Lists

- unordered
- ordered
- Emphasis
  <em>
- Importance
  <strong>
- presentational elements
  b, i, u
- Links
  - email
  - phone
- Description Lists
- Quotations
- Abbreviations
- Contact details
  - address
- Superscript and subscript
- sup & sub
- Representing computer code
  - <code>: For marking up generic pieces of computer code.
  - <pre>: For retaining whitespace (generally code blocks) — if you use indentation or excess whitespace inside your text, browsers will ignore it and you will not see it on your rendered page. If you wrap the text in <pre></pre> tags however, your whitespace will be rendered identically to how you see it in your text editor.
  - <var>: For specifically marking up variable names.
  - <kbd>: For marking up keyboard (and other types of) input entered into the computer.
  - <samp>: For marking up the output of a computer program.
- Times and Dates: <time> element for marking up times and dates in a machine-readable format

## Line breaks and horizontal rules

- <br> creates a line break in a paragraph; it is the only way to force a rigid structure in a situation where you want a series of fixed short lines, such as in a postal address or a poem.
- <hr> elements create a horizontal rule in the document that denotes a thematic change in the text (such as a change in topic or scene). Visually it just looks like a horizontal line.

## Comments

Wrap the code in the special markers <!-- and -->

# CSS

https://developer.mozilla.org/en-US/docs/Web/CSS/Reference

## How to apply your CSS to your HTML

External stylesheet
Internal stylesheet
Inline styles

## Syntax

https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Syntax

Properties: Human-readable identifiers that indicate which stylistic features (e.g. font, width, background color) you want to change.
Values: Each specified property is given a value, which indicates how you want to change those stylistic features (e.g. what you want to change the font, width or background color to.)

## Shorthand

- https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Fundamentals#Font_shorthand
- https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_boxes/Backgrounds#Background_shorthand

## Selectors

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors#Basic_selectors

### Simple Selectors

- Type selector `elementname`
- Class selector `.classname`
- ID selector `#idname`
- Universal selector _, ns|_, _|_, |\*
- Attribute selector `[attr=value]`

## Combinators

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors#Combinators

- Adjacent sibling combinator `A + B`
- General sibling combinator `A ~ B`
- Child combinator `A > B`
- Descendant combinator `A B`

## Pseudo-classes

https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes

## Pseudo-elements

https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements

## Groups of Selectors

https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors#Groups_of_selectors_on_one_rule

## Box Model

- Overflow
- Background clip
- Outline

## Styling Text

https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Fundamentals#Font_style_font_weight_text_transform_and_text_decoration

- Font Styles

  - color
  - family
  - size
  - Weight/Emphasis
    - style
    - weight
    - text transform
    - text decoration
  - Drop Shadows

- Text Layout Styles
  - Text Alignment
  - Line Height
  - Letter and word spacing

Other text properties
https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Fundamentals#Other_properties_worth_looking_at

## Styling Lists

https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Styling_lists

## Styling Links

https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Styling_links

### Link States

- **Link** (unvisited): The default state that a link resides in, when it isn't in any other state. This can be specifically styled using the :link pseudo class.
- **Visited**: A link when it has already been visited (exists in the browser's history), styled using the :visited pseudo class.
- **Hover**: A link when it is being hovered over by a user's mouse pointer, styled using the :hover pseudo class.
- **Focus**: A link when it has been focused (for example moved to by a keyboard user using the Tab key or similar, or programmatically focused using HTMLElement.focus()) — this is styled using the :focus pseudo class.
- **Active**: A link when it is being activated (e.g. clicked on), styled using the :active pseudo class.

## Styling Boxes

### Backgrounds

https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_boxes/Backgrounds

## Styling Tables

https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_boxes/Styling_tables

## Layout

- Floats
- Positioning
- Flexbox
- Grids

## CSS Frameworks
