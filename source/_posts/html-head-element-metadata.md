---
title: 'HTML document structure, head element, and metadata'
tags:
  - web development
  - feynman technique
categories:
  - [series, web dev from the beginning]
  - [web development, front-end, html]
date: 2020-01-28 16:05:19
---


It's not enough to just know how to mark up content using HTML. It's at least equally as important to know how to structure your document well and use the proper metadata. That will make sure your page assets load properly, including stylesheets and JavaScript. It will also help search engines and social media sites process your site correctly.

<!-- more -->

# HTML document structure

A minimal HTML document should look something like this:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>This is an HTML page</title>
  </head>
  <body>
    <!-- content goes here -->
  </body>
</html>
```

As you can see, the whole document is wrapped in an <b>html</b> element. The content visible to the user is contained within the <b>body</b> element.

Two elements remain a mystery at this point, though: the <b>DOCTYPE</b> and the <b>head</b>.

## The DOCTYPE

Once upon a time, in the halcyon days of the early internet, the pioneers of the Web invented the Document Type Definition (<abbr title="Document Type Definition">DTD</abbr>).

The DTD was created to define valid elements of a document written in XML or another <abbr title="Standard Generalized Markup Language">SGML</abbr>-family language.

HTML happens to be a member of the SGML family.

The doctype was conceived as a set of rules that would allow things like machine parsing of HTML code for things like automated error checking.

There were different doctypes for different versions of the HTML specification. They used to look something like this:

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

Nowadays nobody cares about the doctype, but it still has to be there for browsers to properly apply standards to an HTML document. The shortest possible valid doctype for an HTML document is

```html
<!DOCTYPE html>
```

Since that's the simplest way to meet the current standard, that's what we use.

## The head element

The <b>head</b> element is a container for various types of metadata about the document.

Most metadata is primarily written for machines. This is in contrast to the content held in the <b>body</b> element, which is primarily for human users.

The rest of this article will go through various kinds of metadata you may find in HTML documents. It is not intended to be an exhaustive list.

# The document language

The main language for the document is actually specified in the <b>lang</b> attribute for the <b>html</b> element:

```html
<html lang="en">
```

You can specify a language for any element, so a single document can have content in multiple languages. It's important to specify languages so the browser renders the content accurately.

While you can define languages on any element, it's a best practice to define a main language on the <b>html</b> element to define the context for the whole document.

# The document charset

The document charset tells the browser how to decode its contents so when the document is rendered on screen it's readable. If the charset isn't set correctly, you could end up with a bunch of unreadable gobbeldygook on screen, and no one wants that.

The most common character encoding is UTF-8, and most web servers and browsers make this their default charset.

Nevertheless, it is wise to explicitly set the character encoding because you never know when exceptions may occur.

# The title element

The title element tells the browser what title to display for the page in its tab. It may also be used by search engines for the link text in the search result entry.

The title is _not_ displayed on screen as part of the page's content, however. That needs to be set inside the document.

# The meta element

You've already seen one way to use the <b>meta</b> element: defining the charset.

The <b>meta</b> element is extremely versatile. It can simulate HTTP headers, which are normally set by the web server. It can also tell search engines and social networks how to display information about the page. It can convey information about the author or organization behind the page, and more.

## Name attribute

Many <b>meta</b> elements have a <b>name</b> attribute. The <b>name</b> attribute specifies what kind of information it contains.

One common <b>name</b> value is "description," which contains the text blurb search engines use to describe the site on the listings page.

Example: a search description

```html
<meta name="description" content="The MDN Web Docs site provides information about Open Web technologies
  including HTML, CSS, and APIs for both Web sites and progressive web apps.">
```

Another is "author," which you can use to identify the author and, if you want, give contact information.

```html
<meta name="author" content="Jason Barr (me@jasonbarr.dev)>
```

The "viewport" meta tag lets developers control the virtual size and scale of a device's screen size. This lets them optimize their app's user interface for different kinds of screens. That allows them to build responsive UIs that scale to different screen sizes and resolutions.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

## Content attribute

The <b>content</b> attribute holds the information described by the element's <b>name</b> or another attribute. See the examples above.

## Http-equiv attribute

The <b>http-equiv</b> attribute emulates an HTTP header.

One common use for this is to force the page to refresh or redirect.

Example: redirect the user to medium.com after 2 seconds

```html
<meta http-equiv="refresh" content="2;url=http://medium.com/" />
```

Note that some users have their browsers set to ignore meta redirects.

## Search engine metadata

In addition to the "description" metadata, search crawlers may use other kinds of metadata. For example, you can tell crawlers not to index your page with a <b>meta</b> element.

```html
<meta name="robots" content="noindex">
```

Note that this will only prevent them from indexing the single page it's on, not your entire site. For that you'll need a <i>robots.txt</i> file.

It will also not keep a crawler from following links to index other pages you've linked to from your page. If you want it to not follow links, add "nofollow" to the above meta element.

It used to be common practice to specify a "keywords" meta element so you could inform search engines of relevant categories for your page. Unfortunately, some people would stuff their keyword meta tags full of hundreds of spammy keywords, rendering them largely useless. Modern search crawlers largely ignore this tag.

## Social media metadata

Some social media sites use proprietary metadata to enhance the user experience when sharing content on their sites or apps.

For example, Facebook has their own Open Graph protocol. Twitter has their own format, as do a few other sites.

Here's the current Open Graph metadata as of the exact time I'm typing this article:

```html
<meta property="og:type" content="article">
<meta property="og:title" content="HTML document structure, head element, and metadata">
<meta property="og:url" content="https://exocortex.jasonbarr.dev/html-head-element-metadata/index.html">
<meta property="og:site_name" content="exocortex">
<meta property="og:description" content="It's not enough to just know how to mark up content using HTML. It's at least equally as important to know how to structure your document well and use the proper metadata. That will make sure">
<meta property="og:locale" content="en_US">
```

## Other metadata

There are several other types of metadata that use the <b>meta</b> element, but the above examples cover the most common usage categories.

# The link element

It would be easy to think the <b>link</b> element is similar to the <b>a</b> element in defining a link that takes you to a different file. In reality, it's more like the opposite: the <b>link</b> element could be said to bring outside files into the current document.

Or, more accurately, the <b>link</b> element specifies relationships between the current page and an external resource of some kind.

The simplest use of <b>link</b> has two attributes: <b>rel</b> and <b>href</b>. The <b>rel</b> attribute defines the relationship, and <b>href</b> gives the URL for the resource.

The two most common uses of <b>link</b> are to import icons and stylesheets.

## Icons

Several clients display icons for a website or app. The most common is the favicon, which is visible in the browser tab a page is loaded in. It may also be shown with a page's title in your bookmarks, like so:

{% img https://mdn.mozillademos.org/files/12351/bookmark-favicon.png '"Source: Mozilla Developer Network" "A Firefox favicon in a browser bookmarks panel"' %}

A favicon link looks something like this:

```html
<link rel="icon" href="favicon.ico" type="image/x-icon">
```

Different devices may use larger icons, icons with higher resolution, and so on. Several Android and Apple devices have their own preferred icon sizes.

## Stylesheets

You also use <b>link</b> to connect an external stylesheet to your page. Assuming you're not just planning to use the default browser styles for your web apps, this is pretty important.

You can connect as many stylesheets as you need. Just remember that each file will have to be downloaded, which adds to the amount of time it takes your app to load and render.

Styles will be applied in the order their links are defined, so if there are conflicts a style in the last linked stylesheet will override one from the first. This can be useful if you're using a CSS library and want to override some of its styles.

Set <b>rel</b> to "stylesheet" to load a stylesheet:

```html
<link rel="stylesheet" href="css/style.css">
```

# Loading JavaScript in the head

You can load JavaScript in either the <b>head</b> or <b>body</b>. The reasons you might do one or the other are beyond the scope of this article, but you use the <b>script</b> element the same either way.

You can use the <b>src</b> attribute to connect an external JavaScript file or define your script inline between the opening and closing <b>script</b> tags, but you can't do both with the same element.

Example: loading an external script file

```html
<script src="js/scripts.js"></script> <!-- note that you MUST have a closing tag -->
```

Example: using inline JavaScript

```html
<script>
  const helloElem = document.getElementById("say-hello");
  const sayHello = name => helloElem.textContent = `Hello, ${name}!`;

  sayHello("Jason");
</script>
```

There's a lot more you can put into your document <b>head</b>, but we've covered most of the common uses.
