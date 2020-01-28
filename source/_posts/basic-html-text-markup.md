---
title: Basic text markup with HTML
tags:
  - web development
  - feynman technique
categories:
  - [series, web dev from the beginning]
  - [web development, front-end, html]
date: 2020-01-27 16:28:16
---

The most common task you'll perform with HTML is marking up text. HTML gives structure and meaning, also known as semantics, to plain text.

<!-- more -->

# Marking up text: the basics

Headings and paragraphs are the most basic way to structure text in HTML. Lists are also very common. You can also mark up text inside a paragraph or other element to give it emphasis or some other shade of meaning.

## Headings and paragraphs

Headings and paragraphs give textual content a structural hierarchy from the top-level heading down to the bottom-level text itself.

Headings start with <b>h1</b> and include numbers all the way to <b>h6</b>. The paragraph element is simply a <b>p</b>.

### Heading and paragraph examples

```html
<h1>This is the top-level heading</h1>

<p>This text goes under the top-level heading, but not under any subheading.</p>

<h2>This is the first subheading</h2>

<p>Here is some more text that describes something relevant to the subheading.</p>

<h3>This is a nested subheading</h3>

<p>The nested subheading is for content related to the h2 subheading, but important enough to merit its own subheading.</p>

<h3>You can have multiple subheadings on a page</h3>

<p>In fact, having multiple subheadings can make your content far easier to read.</p>

<p>In most cases you should only have one top-level h1 heading, though. It should communicate the page's main topic or purpose.</p>
```

### Semantics vs. presentation

Headings are bold by default and descend in size from <b>h1</b> (the largest) to <b>h6</b> (the smallest); however, you should _not_ depend on presentation to know which element is which.

Any element that contains text can be styled to look like a default heading, but those elements would lack the **semantic** qualities of actual headings. They would not be useful to screen readers (for visually impaired users), search crawlers (important for search rankings), or other clients you need to consider when building web pages.

They might look right, but your eyes can deceive you. Consider a <b>span</b> element styled the following way:

```html
<span style="font-size: 32px; font-weight: bold; margin: 21px 0; display: block;">Is this a top level heading?</span>
```

This span will look _identical_ to a top-level heading's default styles:

<span style="font-size: 32px; font-weight: bold; margin: 21px 0; display: block;">Is this a top level heading?</span>

However, a <b>span</b> element is just a container for text; it has no semantics at all.

### Structural hierarchy

The heading and paragraph elements give the text on your page a structured hierarchy. This hierarchy doesn't just give your page an appearance that matches the relative importance of each part of the document (when styled appropriately); it also gives the text semantics that convey the underlying meaning to clients that consume the page.

Whether or not the hierarchy underlying the text is visible to human eyes depends on if the page is styled properly or not. Other clients, including your browser, will know.

Screen readers use a page's semantic hierarchy to give visually-impaired users an outline of the page's content before they read the rest of the page.

A document that isn't properly marked up won't have an outline. The only way for them to know what it contains would be to read the entire page to find out. Needless to say, given the vast array of content available to your users, they're not likely to stay long if that's the case.

A properly structured hierarchy also helps search crawlers understand more fully what your page is about.

That way it can index the page properly and show it to search users as a result when it's relevant to their search.

Search engines are a major driver of traffic for websites, so if you're working for a business or client you'll want to make sure to take advantage of the best techniques for getting your page indexed correctly.

Making sure you properly arrange headings and paragraphs to mark up your text content will help everyone get the most benefit from your web page.

# Lists

After headings and paragraphs, lists may be the most common kind of text markup.

Lists are all over the place: shopping lists, packing lists, lists of directions, and the list goes on.

The two most common list types in HTML are unordered and ordered lists.

## Unordered lists

You use an unordered list when the order of the items doesn't matter for the purpose of the list.

A shopping list is unordered; it doesn't matter what order you get the items in as long as you get them.

To mark up an unordered list, enclose the list in a <b>ul</b> element. Then use an <b>li</b> element for each individual list item.

### Example: a shopping list

```html
<ul>
  <li>A loaf of bread</li>
  <li>A container of milk</li>
  <li>A stick of butter</li>
</ul>
```

### The resulting list

<div style="border: 1px solid black; margin-bottom: 16px; padding: 0 24px;">
  <ul>
    <li>A loaf of bread</li>
    <li>A container of milk</li>
    <li>A stick of butter</li>
  </ul>
</div>

## Ordered lists

Use an ordered list when the order of the items _does_ matter. For example, if you're giving turn-by-turn directions to your house you'd use an ordered list.

To mark up an ordered list, enclose the list in an <b>ol</b> element. Then wrap each individual item in an <b>li</b> element, just like with an unordered list.

### Example: directions

```html
<ol>
  <li>Pull out of the parking lot</li>
  <li>Turn left onto Broadway</li>
  <li>Drive east for 3.2 miles</li>
  <li>Turn left onto Barker Ave.</li>
  <li>The house, 1422 Barker Ave., will be on your left after about 1/4 mile</li>
</ol>
```

### The resulting list

<div style="border: 1px solid black; margin-bottom: 16px; padding: 0 24px;">
  <ol>
    <li>Pull out of the parking lot</li>
    <li>Turn left onto Broadway</li>
    <li>Drive east for 3.2 miles</li>
    <li>Turn left onto Barker Ave.</li>
    <li>The house, 1422 Barker Ave., will be on your left after about 1/4 mile</li>
  </ol>
</div>

## Content inside an li and nesting lists

You can include any additional HTML you need inside an <b>li</b> element.

If your list items need multiple paragraphs with images and multimedia, you can do that.

You can also nest a list inside another list this way.

### Example: a simple recipe with a nested list

```html
<ol start="6">
  <li>Slowly add the milk to the bowl of dry ingredients</li>
  <li>Stir the milk in until the resulting mixture is even</li>
  <li>Pour the mixture into the pan and put it into the oven
    <ul>
      <li>For a crisp, thin crust, bake at the higher temperature for 10 minutes</li>
      <li>For an even texture with no crust bake at the lower temperature for 20 minutes</li>>
    </ul>
  </li>
</ol>
```

### The resulting recipe

<div style="border: 1px solid black; margin-bottom: 16px; padding: 0 24px;">
  <ol start="6">
    <li>Slowly add the milk to the bowl of dry ingredients</li>
    <li>Stir the milk in until the resulting mixture is even</li>
    <li>Pour the mixture into the pan and put it into the oven
      <ul>
        <li>For a crisp, thin crust, bake at the higher temperature for 10 minutes</li>
        <li>For an even texture with no crust bake at the lower temperature for 20 minutes</li>
      </ul>
    </li>
  </ol>
</div>

## Emphasis and importance

The next 2 elements are used to mark text that's emphasized or important.

The <b>em</b> element is used for text meant to be *em*phasized, and the <b>strong</b> element is for text that is **strong**ly important.

A good rule of thumb for these is to read the text in your mind or even say it aloud. Consider using one of these elements wherever you find yourself emphasizing the words.

Note that, while the default styling for these elements is to _italicize_ <b>em</b> and make <b>strong</b> *bold*, the elements are semantic, not presentational. They could be styled differently and still have the same meaning.

### Example

```html
<p>
  He <em>really</em> wanted to go to the circus, but his father <strong>hated</strong> clowns.
</p>
```

### Resulting text

<div style="border: 1px solid black; margin-bottom: 16px; padding: 16px 24px 0;">
  <p>
    He <em>really</em> wanted to go to the circus, but his father <strong>hated</strong> clowns.
  </p>
</div>

## The old i, b, and u elements

In earlier versions of HTML, some elements were defined as presentational. This is partly because use of CSS wasn't as prominent as it is now, but also because the HTML specification has changed a _lot_ over the past 25+ years.

They used to simply mean making text italicized, bold, or underlined, but with HTML5 elements have to have semantic definitions.

Unfortunately, these elements' meanings in the official specification can be confusing so here's a rule of thumb:

Simply use each of them when you would expect to see italics, bold, or underlining in a written text.

Use <b>i</b> to italicize foreign words, or words that are intended to be heard in a different voice&mdash;e.g. a person changes from speaking aloud to thinking.

Use <b>b</b> for things like keywords and product names.

Use <b>u</b> for things like spelling errors where you would expect the text to be underlined.

Be careful with u, though! Web users are strongly conditioned to expect underlined text to be a link. You might want to restyle <b>u</b> elements so the line is dashed or squiggly or something else so it's clear the user is not supposed to click the text.
