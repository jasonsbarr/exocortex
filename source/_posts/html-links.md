---
title: 'Creating links: tips and best practices'
tags:
  - web development
  - feynman technique
categories:
  - - series
    - web dev from the beginning
  - - web development
    - front-end
    - html
date: 2020-01-28 12:36:25
---


Links put the "hypertext" in HTML. Knowing how to make informative, secure hyperlinks is a must-have skill for a web developer.

<!-- more -->

# What links can do

Links are literally what make the Web what it is. You can link your document to any file that's connected to the internet... _anywhere_.

You can link to the beginning of another document or to a specific location inside it. You can even make a whole application available just through a link&mdash;an advantage web apps have over native apps. No installation necessary; just click the link!

# Understanding the a element

To create a link simply wrap content in an <b>a</b> element and put the linked URL in the <b>href</b> attribute:

```html
For a privacy-focused search experience, <a href="https://duckduckgo.com/">visit DuckDuckGo</a>.
```

Result:

For a privacy-focused search experience, <a href="https://duckduckgo.com/">visit DuckDuckGo</a>.

## The title attribute

Use the <b>title</b> attribute to show a tooltip with additional information about the link when the user hovers the mouse over the link.

```html
You can use <a href="https://pages.github.com/" title="Your site is hosted directly in your repository">GitHub Pages</a> to host websites for your projects for free!
```

Result:

You can use <a href="https://pages.github.com/" title="Your site is hosted directly in your repository">GitHub Pages</a> to host websites for your projects for free!

### Using the title attribute well

If the information you want to convey is important for usability of the link itself, put it in the link text instead.

Remember, the tooltip only appears when you hover the mouse over it, which means people who use a keyboard to navigate the web won't be able to see it. This includes many screen reader users and others with accessibility needs.

## Opening links in a new tab

You can force linked documents to open in a new browser window or tab by using the <b>target</b> attribute.

Whether you _should_ do this or not is an open question; some usability experts believe it degrades user experience. Others prefer it though, so use your own best judgment.

```html
This link to <a href="https://google.com" target="_blank" rel="noopener noreferrer">Google</a> opens in a new window or tab.
```

Result:

This link to <a href="https://google.com" target="_blank" rel="noopener noreferrer">Google</a> opens in a new window or tab.

### The target attribute and security

Note the use of the <b>rel</b> attribute above. When you use <b>target</b> you need to also use <b>rel</b> with the value "noopener noreferrer." This prevents a security vulnerability in the event a malicious entity would hijack the page where you click the link.

## Can wrap block elements

The <b>a</b> element is inline, but it can wrap block elements too. This is one of few cases where it's ok to wrap a block element with an inline one.

# URLs and file paths

Web-available files are made available in a host's document root, which maps the server's location to a directory on its filesystem. This mapping is set by the host machine's server configuration.

A file path points to the file's actual location on its host filesystem relative to the document root.

## Relative file paths

A relative file path points to a file's location relative to the document you're currently browsing, as long as the files are on the same host.

There are four ways to write relative file paths.

If a file is in the same directory as your current file, just use the file's name.

If it's in a directory that's below the one your current file is in, list directory names separated by forward slashes until you reach its directory. Then use the file's name.

Example: path/to/directory/file.txt

If it's in a directory above the one your current file is in, use two dots followed by a forward slash for each level you need to move upwards.

Example: ../../file.txt

If it's in a directory on a different branch of the filesystem, you'll need to move upward until you reach a common parent directory. Then move down until you reach the file you're looking for.

Example: ../../../different/branch/file.txt

### Paths to document fragments

You can also use a path to a section inside an HTML document, called a fragment.

To create a linkable fragment in an HTML file, simply use an <b>id</b> attribute on the element at the place you want the link to point.

It's common practice to use a subheading for this location because the text of the subheading can immediately orient the user.

To link to a fragment, append a hash (#) followed by the fragment id to the file path.

## Absolute URLs

An absolute URL points to a file's exact web address. It starts with the protocol, then the domain and any other necessary information to find the document root (e.g. port). Then it lists the file path relative to the document root. Optionally, a URL may end with a query string (used for passing data, which isn't relevant right now) and fragment identifier.

An absolute URL will work the same no matter where on the web it is. If you're linking to a document on a different host, you _must_ use an absolute URL.

## Relative URLs

A relative URL gives the file path relative to the document you're currently browsing. It can only be used for files on the same host.

Note that if the file you're creating the link in ever gets moved, a relative URL will have to be updated. An absolute URL will always work as long as the linked file is in the location specified.

# Best practices for links

Make the wording of the content inside your link clear and descriptive, but also concise.

Don't use "click here" as your link text. Screen reader users may skip from link to link and having several links with the same link text is confusing as hell for them.

Descriptive link text also helps search crawlers accurately index the linked page, which is good for search rankings.

It also helps readers who are skimming your content (as most web users do) quickly identify if they need to click the link or not.

Be absolutely clear about when you're linking to a non-HTML resource. There are few things more annoying than when you click a link, expecting another page to load, and you are instead prompted to download a file.

You also want to make sure users on slower connections don't get stuck trying to stream some massive video file. Trying to watch a 4k UHD video on a 3g mobile connection is not fun.

Finally, use the <b>download</b> attribute when linking to a file you intend the user to download. This ensures the download dialogue pops up and also lets you specify a default filename for the download.

# Links with other protocols besides http://

You can also create links for other protocols.

The mailto: protocol tells the browser to open the user's default email client to send an email to the address specified in the link. You can also use the query string to specify additional information. For example, the following link:

```html
<a href="mailto:john@example.com?subject=This%20is%20a%20test&cc=me@domain.net">Email John</a>
```

Will open the user's mail client, start the process for composing an email to <i>john@example.com</i>, give it the subject line "This is a test," and add <i>me@domain.net</i> to the cc: list.

You can also set bcc: and text for the email body using the bcc and body query parameters, respectively.

If there are spaces in any of your query string values you'll need to percent-encode them, as you see above. You may need to encode other symbols as well. Here's a <a href="https://www.url-encode-decode.com/">free tool to encode or decode URL text</a>. You may find it helpful.

Other applications may have their own protocols that tells the browser to open them. For example, Skype uses the skype: protocol.

You can link to a location on an <abbr title="File Transfer Protocol">FTP</abbr> server using the ftp:// protocol. Most browsers will support this use.

Link to a file on the user's own computer with file://.

There are other URL protocols as well, but these should cover most common use cases.
