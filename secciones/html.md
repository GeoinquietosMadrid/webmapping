# HTML, CSS & Markdown

## 1. HTML

## 2. CSS

## 3. Markdown

### 3.1. What is Markdown?

[Markdown](http://daringfireball.net/projects/markdown/) is a way to style text on the web. You control the display of the document; formatting words as bold or italic, adding images, and creating lists are just a few of the things we can do with Markdown. Mostly, Markdown is just regular text with a few non-alphabetic characters thrown in, like `#` or `*`.

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

