# HTML, CSS & Markdown

## 1. HTML

### 1.1. What is HTML?

**HyperText Markup Language** (**HTML**) is the standard markup language for creating web pages and web applications. With Cascading Style Sheets (CSS), and JavaScript, it forms a triad of cornerstone technologies for the World Wide Web. Web browsers receive HTML documents from a webserver or from local storage and render them into multimedia web pages. HTML describes the structure of a web page semantically and originally included cues for the appearance of the document.

### 1.2. HTML elements

HTML consists of a series of **elements**, which you use to enclose, or wrap, different parts of the content to make it appear a certain way, or act a certain way. The enclosing tags can make a word or an image a hyperlink to somewhere else, can italicize words, and can make font bigger or smaller, and so on. 

Let's explore a (paragraph) element a bit further:

![element](https://mdn.mozillademos.org/files/9347/grumpy-cat-small.png)

Elements can also have **attributes**, which look like this:

![attributes](https://mdn.mozillademos.org/files/9345/grumpy-cat-attribute-small.png)

### 1.3. Nesting elements

You can put elements inside other elements too — this is called **nesting**:

```html
<p>My cat is <strong>very</strong> grumpy.</p>
```

### 1.4. Empty elements

Some elements have no content, and are called **empty elements**. Take the `<img>` element we already have in our HTML:

```html
<img src="images/firefox-icon.png" alt="My test image">
```

### 1.5. Anatomy of an HTML document

That wraps up the basics of individual HTML elements, but they aren't very useful on their own. Now we'll look at how individual elements are combined to form **an entire HTML page**:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <p>My cat is <strong>very</strong> grumpy.</p>
    <img src="images/firefox-icon.png" alt="My test image">
  </body>
</html>
```

### 1.6. Marking up text

This section will cover some of the basic HTML elements you'll use for marking up text.

#### Headings

```html
<h1>My main title</h1>
<h2>My top level heading</h2>
<h3>My subheading</h3>
<h4>My sub-subheading</h4>
```

#### Paragraphs

```html
<p>This is a single paragraph</p>
```

#### Lists

* *Unordered lists* are for lists where the order of the items doesn't matter, like a shopping list. These are wrapped in a `<ul>` element.

* *Ordered lists* are for lists where the order of the items does matter, like a recipe. These are wrapped in an `<ol>` element.

Each item inside the lists is put inside an `<li>` (list item) element.

```html
<p>At GeoInquietos Madrid, we’re a community of</p>
    
<ul> 
  <li>cartographers</li>
  <li>developers</li>
  <li>GIS technicians</li>
  <li>data journalists</li>
</ul>

<p>sharing our love for maps and OS geo-applications.</p>
```

#### Links

Links are very important — they are what makes the Web A WEB. To add a link, we need to use a simple element — <a> — the a being short for "anchor".

```html
<a href="http://geoinquietos.org/">GeoInquietos Web</a>
```

## 2. CSS

### 2.1. What is CSS?

**Cascading Style Sheets** (**CSS**) is a style sheet language used for describing the presentation of a document written in a markup language.

### 2.2. How does CSS affect HTML?

Web browsers apply **CSS rules** to a document to affect how they are displayed. A CSS rule is formed from:

* A set of **properties**, which have **values** set to update how the HTML content is displayed, for example I want my element's width to be 50% of its parent element, and its background to be red.

* A **selector**, which selects the element(s) you want to apply the updated property values to. For example, I want to apply my CSS rule to all the paragraphs in my HTML document.

A set of CSS rules contained within **a stylesheet** determines how a webpage should look.

### 2.3. CSS declarations

Setting CSS properties to specific values is the core function of the CSS language. The CSS engine calculates which **declarations** apply to every single element of a page in order to appropriately lay it out and style it. What is important to remember is that both properties and values are case-sensitive in CSS. The property and value in each pair is separated by a colon (:).

![declarations](https://mdn.mozillademos.org/files/3665/css%20syntax%20-%20declaration.png)

Declarations are grouped in **blocks**, with each set of declarations being wrapped by an opening curly brace, (`{`) and a closing one (`}`).

Each declaration contained inside a declaration block has to be separated by a semi-colon (`;`), otherwise the code won't work (or will at least give unexpected results.)

![block](https://mdn.mozillademos.org/files/3667/css%20syntax%20-%20declarations%20block.png)

### 2.4. CSS selectors and rules

We are missing one part of the puzzle — we need to discuss how to tell our declaration blocks which elements they should be applied to. This is done by prefixing each declaration block with a **selector** — a pattern that matches some elements on the page. The associated declarations will be applied to those elements only. The selector plus the declaration block is called a **ruleset**, or often simply just a **rule**.

![selector](https://mdn.mozillademos.org/files/3668/css%20syntax%20-%20ruleset.png)

### 2.5. Methods of adding CSS to HTML

#### Linking to a separate CSS file

This is the most common method of attaching CSS rules to an HTML document. With this method all of your style rules are contained in a single text file that is saved with the .CSS extension. This file is saved on your server and you link to it directly from each HTML file. The link is just a simple line of HTML that you put in the <head> section of your HTML document, it looks like this:

```html
  <link rel="stylesheet" type="text/css" href="style.css">
```

#### Embedding CSS into the HTML

You can also embed CSS rules directly into any HTML page. To do this you need to add the following code to the <head> of your HTML document:

```html
<style type="text/css">

 	html, body, #map{
 		height: 100%;
 		padding: 0;
 		margin: 0;
 	}

</style>
```

### Adding Inline CSS to HTML tags

Style rules can also be added directly to any HTML element. To do this you simply add a style parameter to the element and enter your style rules as the value. Here is an example of a heading with red text and a black background:

```html
<h2 style="color: red; background: black;">This is a red heading with a black background</h2>
```

### Importing a CSS file from within CSS

Another interesting way to add CSS to a HTML page is with the import rule. This lets us attach a new CSS file from within CSS itself. Let's look at an example of how this is done then I will show a practical example of when you might use this method. To import a new CSS file **from within** CSS simply use the following rule:

```css
@import "newstyles.css";
```

## 3. Markdown

### 3.1. What is Markdown?

**[Markdown](http://daringfireball.net/projects/markdown/)** is a way to style text on the web. You control the display of the document; formatting words as bold or italic, adding images, and creating lists are just a few of the things we can do with Markdown. Mostly, Markdown is just regular text with a few non-alphabetic characters thrown in, like `#` or `*`.

You can use Markdown most places around GitHub:

* Gists
* READMEs
* Comments in Issues and Pull Requests
* Files with the `.md` or `.markdown` extension

### 3.2. Syntax Guide

You can follow this guide with a Markdown sandbox application such as [Dillinger](http://dillinger.io/) or [StackEdit](https://stackedit.io/editor).

#### Text

* Bold: \*\*hello\*\* or \_\_hello\_\_ will be displayed as **hello**
* Italics: \*hello\* or \_hello\_ will be displayed as _hello_
* Links: `\[link to GitHub!\](http://github.com)` will be displayed as [link to GitHub!](http://github.com)

#### Quotes

\> This is a quote.

> This is a quote.

#### Headers

Headers start with `#`.

# This is an `<h1>` tag
## This is an `<h2>` tag
###### This is an `<h6>` tag

#### Lists

Sometimes you want numbered lists (`1.`, `2.`, etc.):

1. One
2. Two
3. Three

Sometimes you want bullet points (`*`):

* Start a line with a star
* Profit!

Alternatively (`-`),

- Dashes work just as well
- And if you have sub points, put two spaces before the dash or star:
  - Like this
  - And this

#### Images

If you want to embed images, use the same syntax as link but with an exclamation sign before (`!`). So `\!\[markdown\](https://github.com/GeoinquietosMadrid/webmapping/blob/master/img/markdown.png)` will be displayed as:

![markdown](https://github.com/GeoinquietosMadrid/webmapping/blob/master/img/markdown.png)

#### Code

There are many different ways to style code with GitHub's markdown. If you have inline code blocks, wrap them in backticks (\`): `var example = true`.  If you've got a longer block of code, you can indent with four spaces:

    if (isAwesome){
      return true
    }

GitHub also supports something called code fencing, which allows for multiple lines without indentation (\`\`\`):

```
if (isAwesome){
  return true
}
```

And if you'd like to use syntax highlighting, include the language (javascript, sql, css, python...):

```javascript
if (isAwesome){
  return true
}
```

## 4. References

* [HTML](https://en.wikipedia.org/wiki/HTML), [CSS](https://en.wikipedia.org/wiki/Cascading_Style_Sheets) and [Markdown](https://en.wikipedia.org/wiki/JavaScript) Wikipedia pages
* [Mozilla Developer Network](https://developer.mozilla.org/)
* [GitHub Guides](https://guides.github.com/)
* [Matthew James Taylor blog](http://matthewjamestaylor.com/blog/)

