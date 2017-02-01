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

## 3. Markdown

### 3.1. What is Markdown?

**[Markdown](http://daringfireball.net/projects/markdown/)** is a way to style text on the web. You control the display of the document; formatting words as bold or italic, adding images, and creating lists are just a few of the things we can do with Markdown. Mostly, Markdown is just regular text with a few non-alphabetic characters thrown in, like `#` or `*`.

You can use Markdown most places around GitHub:

* Gists
* READMEs
* Comments in Issues and Pull Requests
* Files with the `.md` or `.markdown` extension

### 3.2. Syntax Guide

#### Text

* Bold: \*\*hello\*\* or \_\hello\_\_ will be displayed as **hello*
* Italiks: \*hello\* ó \hello\_ will be displayed as _hello_
* Links: \[link to GitHub!\](http://github.com) will be displayed as [link to GitHub!](http://github.com)

#### Quotes

\> This is a quote.

> This is a quote.

#### Headers

Headers start with `#`.

# This is an <h1> tag
## This is an <h2> tag
###### This is an <h6> tag

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

If you want to embed images, use the same syntax as link but with an exclamation sign before (`!`):

![markdown](https://github.com/GeoinquietosMadrid/webmapping/blob/master/img/markdown.png)

#### Code

There are many different ways to style code with GitHub's markdown. If you have inline code blocks, wrap them in backticks: `var example = true`.  If you've got a longer block of code, you can indent with four spaces:

    if (isAwesome){
      return true
    }

GitHub also supports something called code fencing, which allows for multiple lines without indentation:

```
if (isAwesome){
  return true
}
```

And if you'd like to use syntax highlighting, include the language:

```javascript
if (isAwesome){
  return true
}
```

## 4. References

* [HTML](https://en.wikipedia.org/wiki/HTML), [CSS](https://en.wikipedia.org/wiki/Cascading_Style_Sheets) and [Markdown](https://en.wikipedia.org/wiki/JavaScript) Wikipedia pages
* [Mozilla Developer Network](https://developer.mozilla.org/)
* [GitHub Guides](https://guides.github.com/)

