---
title: "1.1 - The basics of HTML"
categories:
  - [web development, front-end, html]
  - [series, web dev from the beginning]
tags:
  - web development
  - feynman technique
---

# What is HTML?

<abbr title="HyperText Markup Language">HTML</abbr> is not a programming language. It is a markup language that tells a client, like your browser, how to structure the content in the document.

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
<div
  style="border: 1px solid black; margin-bottom: 16px; padding: 16px 24px 0;"
> <!-- style attribute contains CSS, ignore for now -->
  <p>
    This is a paragraph. It contains text and possibly additional markup to
    <em>emphasize</em> text or <a href="https://google.com">link</a> to
    another HTML page.
  </p>
</divstyle="border:>
```

### The result

<div style="border: 1px solid black; margin-bottom: 16px; padding: 16px 24px 0;">
  <p>
    This is a paragraph. It contains text and possibly additional markup to
    <em>emphasize</em> text or <a href="https://google.com">link</a> to
    another HTML page.
  </p>
</div>

As you can see, most whitespace (e.g. spaces, tabs, newlines) has no effect on the result. The first whitespace tells the browser to move onto the next token. After that, all whitespace characters are ignored.
