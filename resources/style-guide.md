# Style Guide
This document contains guidelines and best practices for front-end development using HTML and CSS.  

Something off, or missing?  Contribute to this document by submitting your questions using the [issues feature](https://github.com/theaccordance/web-design/issues) within this repo.


## Table of Contents
1. [Project](#Project)
  1. [Naming Convention](#naming-convention)
  1. [Organization](#project-organization)
1. [HTML](#html)
  1. [Syntax](#html-syntax)
  1. [HTML5 Doctype](#html5-doctype)
  1. [Character Encoding](#character-encoding)
  1. [Including Stylesheets](#including-stylesheets)
  1. [Attributes](#attributes)
    1. [Naming](#naming)
    1. [Order](#attribute-order)
  1. [Reducing Markup](#reducing-markup)
1. [CSS](#css)
  1. [Syntax](#css-syntax)
  1. [Selectors](#selectors)
  1. [Declarations](#declarations)
    1. [Single Declarations](#single-declarations)
    1. [Multiple Declarations](#multiple-declarations)
    1. [Order](#declaration-order)
  1. [Organization](#organization)
1. [References](#references)

## Project

### Naming Convention
Names for your project, files, and folders should be short, lowercase, and use dashes instead of spaces.  
```
\\ Incorrect
My Really Awesome Project/
Facebook Profile Picture.jpg

\\ Not Ideal
my-really-awesome-project/
facebook-profile-picture.jpg

\\ Ideal
my-project/
avatar.jpg
```

<h3 id="project-organization">Organization</h3>
Keep your files organized using the *File-By-Type* approach.  Files kept in the following folders:

| Path | Types of Files | File Types
| :---: | :---: | :---:
| `my-project/` | HTML Documents | `.html`
| `my-project/css` | Stylesheets | `.css`
| `my-project/fonts` | Web Fonts | `.eot` `.ttf` `woff`
| `my-project/img` | Images | `.jpg` `.gif` `.png` `.svg`
| `my-project/js` | Scripts | `.js`

>**Tip:** Avoid adding sub-folders to buckets with less than 25 files.   

## HTML

<h3 id="html-syntax">Syntax</h3>
If an element has no nested elements, its closing tag can remain on the same line as the opening tag.
```html
<!-- Incorrect -->
<div><p>Foo</p></div>

<!-- Not Ideal -->
<div>
</div>

<!-- Correct -->
<div></div>

```

Nested elements should start on a new line and be indented within the parent element.  
```html
<!-- Incorrect -->
<div><p>Foo</p></div>

<!-- Incorrect -->
<div>
<p>Foo</p>
</div>

<!-- Correct -->
<div>
    <p>Foo</p>
</div>
```

Always use "double" quotes, never 'single' quotes, on attributes.
```html
<!-- Incorrect -->
<div class='single-quote'></div>

<!-- Correct -->
<div class="double-quote"></div>
```

Include a trailing slash in self-closing elements
```html
<!-- Incorrect -->
<img src="foo.jpg" class="bar" >

<!-- Correct -->
<img src="foo.jpg" class="bar" />
```

Do not omit optional closing tags:
```html
<!-- Incorrect -->
<ul>
    <li>Foo
    <li>Bar
    <li>Baz
</ul>

<!-- Correct -->
<ul>
    <li>Foo</li>
    <li>Bar</li>
    <li>Baz</li>
</ul>
```

### HTML5 Doctype
Every html document should start with the DOCTYPE tag.
```html
<!-- Incorrect -->
<html>
    <head>...</head>
    <body>...</body>
<html>

<!-- Correct -->
<!DOCTYPE html>
<html>
    <head>...</head>
    <body>...</body>
<html>
```

> **Note:** Doctype does not have a closing tag

### Character Encoding
Quickly and easily ensure proper rendering of your content by declaring an explicit character encoding. When doing so, you may avoid using character entities in your HTML, provided their encoding matches that of the document (UTF-8).
```html
<head>
  <meta charset="UTF-8">
</head>
```

### Including Stylesheets
Stylesheets are nested in the `<head>` section of your HTML document.
```html
<!-- Incorrect -->
<!DOCTYPE html>
<html>
    <head>...</head>
    <body>
        <link rel="stylesheet" href="css/style.css">
    </body>
<html>

<!-- Correct -->
<!DOCTYPE html>
<html>
    <head>
        <link rel="stylesheet" href="css/style.css">
    </head>
    <body>...</body>
<html>
```

### Attributes

#### Naming
For unique attributes like `id` & `name` should follow the `camelCasing` convention.
```html
<!-- Incorrect -->
<section id="foo-bar">...</section>

<!-- Correct -->
<section id="fooBar">...</section>
```

>**Tip:** Avoid excessive use of Ids by applying them only to elements which represent major sections or unique components of your document.

Class names should be formatted using lowercase and dashes.
```html
<!-- Incorrect -->
<img class="fooBar" src="img/baz.jpg" />

<!-- Incorrect -->
<img class="foo_bar" src="img/baz.jpg" />

<!-- Correct -->
<img class="foo-bar" src="img/baz.jpg" />
```


<h4 id="attribute-order">Order</h4>
HTML attributes should come in this particular order for easier reading of code:
- `id`, `name`
- `class`
- `src`, `for`, `type`, `href`, `value`
- `data-*`
- `title`, `alt`
- `role`, `aria-*`

Attributes which uniquely identify an element (`id`, `name`) should come first for ease of readability, followed by classes, which are typically the most common attribute found across all elements in an HTML document.
```html
<!-- Incorrect -->
<img src="img/foo.jpg" id="foo" class="bar baz" />

<!-- Correct -->
<img id="foo" class="bar baz" src="img/foo.jpg" />
```

### Reducing Markup
Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML.
```html
<!-- Not so great -->
<section>
    <div class="row">
        <div class="col-left category">...</div>
        <div class="col-right category">...</div>
    </div>
    <div class="row">
        <div class="col-left category">...</div>
        <div class="col-right category">...</div>
    </div>
</section>

<!-- Better -->
<section>
    <div class="row">
        <div class="col-left category">...</div>
        <div class="col-right category">...</div>
        <div class="col-left category">...</div>
        <div class="col-right category">...</div>
    </div>
</section>
```



## CSS

<h3 id="css-syntax">Syntax</h3>
Include one space before the opening brace of declaration blocks for readability.
```css
// Incorrect
.foo{display: block;}

// Correct
.foo {display: block;}
```

For each declaration within a declaration block:
- Include one space after `:` for each declaration
- Do not include one space before `:` for each declaration
- End all declarations with a semi-colon
```css
// Incorrect
.foo {display:block;}

// Incorrect
.foo {display : block;}

// Incorrect
.foo {display: block}

// Correct
.foo {display: block;}
```

Declarations with multiple property values should include a space after each comma
```css
// Incorrect
.foo {box-shadow: 0 1px 2px #ccc,inset 0 1px 0 #fff;}

// Correct
.foo {box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;}
```

Avoid specifying units for zero values
```css
// Incorrect
.foo {margin: 0px;}

// Correct
.foo {margin: 0;}
```

### Selectors
Keep selectors short and strive to limit the number of elements in each selector to three.
```css
// Incorrect
section ul.nav li a {text-decoration: none;}

// Correct
ul.nav a {text-decoration: none;}
```

### Declarations

#### Single Declarations
Selectors with a single declaration can be kept on a single line.
```css
// Less ideal
.foo {
    margin: 0px;
}

// More ideal
.foo {margin: 0;}
```

#### Multiple Declarations
For selectors with multiple declarations:
- Each declaration should appear on its own line
- Declarations are nested within the selector block
- Place closing braces of declaration blocks on a new line
```css
// Incorrect
.foo {display: block; position: relative;}

// Incorrect
.foo {
display: block;
position: relative;
}

// Incorrect
.foo {
    display: block;
    position: relative;}

// Correct
.foo {
    display: block;
    position: relative;
}
```

<h4 id="declaration-order">Order</h4>
Declarations should be arranged alphabetically within selectors since in-browser developer tools will list declarations this way.
```css
// Incorrect
.foo {
    position: relative;
    top: 0;
    left: 12px;
    display: block;
}

// Correct
.foo {
    display: block;
    left: 0;
    position: relative;
    top: 0;
}
```

### Organization
Organize sections of code by component.
```css
// Incorrect
header {
    background-color: #034f80;
    display: block;
}

footer {
    background-color: #000000;
}

header nav ul {list-style: none;}

// Correct
header {
    background-color: #034f80;
    display: block;
}

header nav ul {list-style: none;}

footer {
    background-color: #000000;
}
```

- - -

Heavily inspired by [@mdo's Code Guide](http://codeguide.co/). Made with :heart:️ in Chicago.

Open Source under MIT.  Copyright 2015 [Joe Mainwaring](http://joemainwaring.com).
