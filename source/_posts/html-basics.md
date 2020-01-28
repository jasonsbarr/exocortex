---
title: The basics of HTML
tags:
  - web development
  - feynman technique
categories:
  - - web development
    - front-end
    - html
  - - series
    - web dev from the beginning
date: 2020-01-27 16:23:34
---

<abbr title="HyperText Markup Language">HTML</abbr> is not a programming language. It is a markup language that tells a client, like your browser, how to structure the content in the document.

<!-- more -->

# What is HTML?

An HTML document consists of a series of nested elements that enclose and mark up its content so the client processes it in a particular way.

HTML is not case sensitive as a language, but the convention is to always write HTML elements in lowercase. This promotes readability and may also prevent errors with some clients.

# HTML elements

HTML documents are made of elements. An HTML element is a piece of markup that carries a particular meaning for its enclosed content and/or other data. Most HTML elements enclose content between their opening and closing tags.

## Anatomy of an HTML element

Every HTML element has its opening tag. Most elements also enclose content and end with a closing tag, like so:

{% img https://mdn.mozillademos.org/files/9347/grumpy-cat-small.png "A paragraph element, from MDN" "paragraph-element" %}

## Nesting elements

You can nest HTML elements inside other elements. To do so, make sure to close them in the reverse order of when they were opened, like this:

```html
<p>This is a paragraph with <em>emphasized</em> text.</p>
```

Failing to properly nest your elements can cause unexpected results that may be difficult to debug.

## Example

### The code

```html
<p>
  This is a paragraph. It contains text and possibly additional markup to
  <em>emphasize</em> text or <a href="https://google.com">link</a> to
  another HTML page.
</p>
```

### The result

<div style="border: 1px solid black; margin-bottom: 16px; padding: 16px 24px 0;">
  <p>
    This is a paragraph. It contains text and possibly additional markup to
    <em>emphasize</em> text or <a href="https://google.com">link</a> to
    another HTML page.
  </p>
</div>

As you can see, most whitespace (e.g. spaces, tabs, newlines) has no effect on the result. The first whitespace character tells the browser to move onto the next token (a word or symbol that means something in HTML). After that, all whitespace characters are ignored.

# Two kinds of HTML elements

Historically the HTML specification has divided elements up into two categories: block and inline.

Even though these categories are no longer in the official spec, they're still useful for understanding how to use HTML.

## Block elements

Block elements visually form a visible block on the page by default. That means there is a clear break with the content that comes both before and after a block element, and it spans the entire width of the page.

Block elements tend to have some kind of structural significance. They mark off sections of a page, headings, paragraphs, and so on.

They are often nested inside other block elements, but you shouldn't place them inside inline elements.

## Inline elements

Inline elements are often found inside a block element, though they can also be nested inside other inline elements.

They surround particular bits of content to mark them up for the document to be read by a browser or other client.

Inline elements often tell the browser what a piece of content means, for example the <b>em</b> element shows its content should be _emphasized_. Text inside an <b>em</b> element is italicized by default.

## These categories are obsolete

They were used in previous versions of HTML where semantics and presentation weren't as clearly set apart as they are in HTML5.

As long as there has been CSS it's been possible to change the elements' styling, but people often misunderstood the purpose of the names "block" and "inline."

It was too easy to confuse block and inline _elements_ with the block and inline _values_ of the CSS <b>display</b> property.

Because of this confusion and the push to define elements in terms of their semantics, HTML5 does not use these categories.

Nonetheless, they are still a convenient shorthand to help you understand how to use different kinds of HTML elements.

# Void elements

Unlike most elements, which take some kind of content between the opening and closing tags, void elements are empty. They hold no content. Their values and other properties are defined by their internal data, which are called <b>attributes</b>.

For example, an <b>img</b> element is void. The image value is determined by its <b>src</b> attribute, which gives the URL for the image file.

## Example

```html
<img src="https://images.unsplash.com/photo-1502759683299-cdcd6974244f?auto=format&fit=crop&w=440&h=220&q=60" alt="Palm trees at sunset">
```

## Result

<img src="https://images.unsplash.com/photo-1502759683299-cdcd6974244f?auto=format&fit=crop&w=440&h=220&q=60" alt="Palm trees at sunset">

# Attributes

The <b>src</b> above that determines the image to be displayed is one example of an HTML <b>attribute</b>.

Attributes contain data about the element to which they are attached. This data is held in addition to any content the element may contain.

There are some global attributes, like <b>class</b>, that can be defined on any element.

Other attributes can only be defined on certain elements or types of elements.

## Boolean attributes

Boolean attributes have no value. The presence of the attribute's name itself is enough to define it.

For example, the <b>disabled</b> attribute on a form <b>input</b> element sets the field so it cannot have text entered into it.

### Example

```html
<label for="disabled-input">
  Disabled
  <input style="display: block;" id="disabled-input" type="text" disabled>
</label>
<label for="working-input">
  Working
  <input style="display: block;" id="working-input" type="text">
</label>
```

### Result

Notice the difference: the first <b>input</b> is disabled, but the second is not. You can type in the second one.

Also note how the <b>input</b> elements, which are inline elements, are styled with <i>display: block</i>. That shows how you can't depend on an element's appearance to categorize it.

<div style="border: 1px solid black; margin-bottom: 16px; padding: 16px 24px;">
  <label style="display: block;" for="disabled-input">
    Disabled:
    <input id="disabled-input" type="text" disabled>
  </label>
  <label style="display: block;" for="working-input">
    Working:
    <input id="working-input" type="text">
  </label>
</div>

## Attribute style

In some cases the quotation marks around an attribute's value are optional. As a general rule you should include them anyway to avoid possible problems.

It doesn't matter if you use single or double quotes around a value, as long as the start and end quote are the same. If you need to enclose a particular kind of quote in the value itself, wrap the value in the other kind of quote.

# Including special characters

Since <, >, ', ", and & all have special meaning as part of the HTML syntax, you have to use HTML entity references to make them appear on screen.

HTML entities begin with &, which is followed by a code, and then terminate with a semicolon.

You can also use an HTML entity for a non-breaking space, which forces the browser to treat it as a space character instead of regular whitespace.

<table>
  <thead>
    <tr>
      <th>Literal character</th>
      <th>HTML entity</th>
    </tr>
    <tr>
      <td><</td>
      <td>&amp;lt;</td>
    </tr>
    <tr>
      <td>></td>
      <td>&amp;gt;</td>
    </tr>
    <tr>
      <td>'</td>
      <td>&amp;apos;</td>
    </tr>
    <tr>
      <td>"</td>
      <td>&amp;quot;</td>
    </tr>
    <tr>
      <td>&</td>
      <td>&amp;amp;</td>
    </tr>
    <tr>
      <td> (blank space)</td>
      <td>&amp;nbsp;</td>
    </tr>
  </thead>
</table>

There are many other HTML entities, but if your document is encoded in UTF-8 you can just use the literal characters for them.

# Comments

Comments are ignored by the browser. You can use them to put notes for yourself or other developers about how the code works, why you made certain design choices, and so on.

A comment starts with &lt;!-- and ends with --&gt;.

```html
<!-- I am inside an HTML comment -->
```
