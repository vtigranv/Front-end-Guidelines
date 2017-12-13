# Front-end Guidelines

## Introduction
During my 15 years of experience in web development, I’ve worked with various companies, from enterprise-level to startups, and I’ve worked with many, many fellow software engineers along the way. One of the most common and important problems I’ve came across in my projects has been failure to write clean and easy-to-understand code. 
Even the best developers from top-notch companies don’t always follow best practices and write code which can be cleaned and optimized.

## Problems and consequences of messy and dirty code
> “Source code is akin to financial debt. Suppose you want to buy a house to live in. Most people don’t have the financial wherewithal to pay cash for a house, so you take out a mortgage instead. But the mortgage itself is not a great thing to have. It’s a liability. You have to pay interest on your debt every month. You always want your mortgage to be as small as possible while still allowing you to buy a house that meets your needs. But if you don’t do some careful thinking about the terms and implications of your mortgage before you buy a house, you can wind up in a load of trouble. It’s possible to end up underwater in a situation where your debt is actually bigger than your house is worth.

> So too in web development. The code has ongoing costs. You have to understand it, you have to maintain it, you have to adapt it to new goals over time. The more code you have, the larger those ongoing costs will be. It’s in our best interest to have as little source code as possible while still being able to accomplish our business goals.”
 
 
Quoted from an old but still relevant blog post: https://blogs.msdn.microsoft.com/elee/2009/03/11/source-code-is-a-liability-not-an-asset/


## Table of Contents

  ### Code styling  ![Code Styling](https://img.shields.io/badge/-Code%20Styling-green.svg)
  1. [File structure](#file-structure)
  1. [Code validation](#code-validation--)
  1. [Alternative tag of images](#use-alternative-text-on-img-tags-for-clean-code-principles-validity--)
  1. [kebab-case names](#kebab-case-names--)
  1. [Meaningful, short names of classes](#meaningful-short-names-of-classes--)
  1. [Type attributes](#remove-type-attributes--)
  1. [Specific classes](#use-specific-classes-when-necessary--)
  1. [Parent element classes](#add-a-class-to-the-parent-element--)
  1. [Zero values without units](#drop-units-from-zero-values--)
  1. [Use of hr tag](#use-an-hr-tag--)
  1. [CSS height and width](#css-without-fixed-height-and-width--) 
  ### HTML ![HTML](https://img.shields.io/badge/-HTML-e24e30.svg)
  1. [Markup based HTML](#try-to-have-a-front-end-that-is-as-markup-based-as-possible--)  
  1. [Unnecessary wrappers in HTML](#avoid-using-unnecessary-wrappers-in-html--) 
  1. [Atomic classes](#use-atomic-classes-for-styling--) 
  1. [Semantic elements](#make-use-of-semantic-elements--) 
  1. [HTML5 tags](#use-html5-tags--) 
  ### CSS ![CSS](https://img.shields.io/badge/-CSS-1572B6.svg)
  1. [A > B selector](#a--b-selector--)
  1. [CSS preprocessors](#use-a-css-preprocessor--) 
  1. [Group selectors or @extend in SASS](#use-extend-in-sass-or-group-selectors--)
  1. [rem units](#use-rem-units--) 
  1. [CSS rule without affected other elements](#before-writing-a-css-rule-think-about-which-element-will-be-affected--)
  1. [Look for existing CSS rules and variables](#look-for-existing-css-rules-and-variables-before-writing-new-ones--) 
  1. [Specific rules](#use-specific-rules--) 
  1. [Shorthand properties and values](#use-shorthand-properties-and-values--) 
  1. [em instead of px](#em-instead-of-px-for-line-height--)  
  ### Bootstrap  ![Bootstrap](https://img.shields.io/badge/-Bootstrap-7142A8.svg)
  1. [More Bootstrap classes](#use-bootstrap-classes-as-much-as-possible--)  
  1. [One parent item in SCSS ](#use-parent-item-just-once-in-scss--)  
  1. [Customizing properly framework](#customize-your-framework-properly--)
  1. [.container fixed width](#dont-overwrite-container-width--)  
  1. [Bootstrap 4 classes](#use-bootstrap-4-classes-and-write-less-css--)  
  1. [Same value for col-X](#remove-col-md-x-and-col-lg-x-if-col-sm-x-has-same-value-for-x--) 
  1. [Use of .col-xs-12](#dont-use-col-xs-12--) 
  1. [normalize.css](#dont-use-resetcss-use-normalizecss-instead)
  1. [Wrapping Up](#wrapping-up)
 
 
 ###
## Code styling

## File Structure

If you are going to develop a big app, then you need to take care of the file structure. It can, or rather should, look like this:

![Good example of file structure in SCSS](https://raw.githubusercontent.com/vtigranv/Front-end-Guidelines/master/assets/file-structure.png)


### Code validation  ![Code Styling](https://img.shields.io/badge/-Code%20Styling-green.svg)

Try to always check your code with [HTML](https://validator.w3.org/) and [CSS](https://jigsaw.w3.org/css-validator/) validators

###### ⚠ Bad Code

  ```
  <figure>
    <div>
      <img src="demo.jpg" alt="">
      <figcaption>
        <h2>Hello world</h2>
      </figcaption>
    </div>
  </figure>

  <picture>
    <source src="demo.webp" type="image/webp">
    <img src="demo.jpg" alt="">
  </picture>

  <details>
    <header>
      <summary>Expand details</summary>
    </header>
    <p>All content goes here</p>
  </details>

  p {
    font: 400 inherit/1.125 serif;
  }
  ```

###### ✅ Good Code

  ```html
  <figure>
    <img src="demo.jpg" alt="">
    <!-- figcaption should be child of figure element, not div -->
    <figcaption>
      <h2>Hello world</h2>
    </figcaption>
  </figure>

  <picture>
    <!-- source should have srcset attribute -->
    <source srcset="demo.webp" type="image/webp">
    <img src="demo.jpg" alt="">
  </picture>

  <details>
    <!-- summary is not allowed as child of header -->
    <summary>Expand details</summary>
    <p>All content goes here</p>
  </details>
  ```
  ```css
  p {
    font-weight: 400;
    font-size: inherit;
    line-height: 1.125;
    font-family: serif;
  }
  ```
  
**[🔝 ](#table-of-contents)**
###
###
######
----
### Use alternative text on `<img>` tags for clean code principles validity  ![Code Styling](https://img.shields.io/badge/-Code%20Styling-green.svg)
  
 This attribute plays vital role for SEO, search engines, web crawlers, screen readers, etc.
  
###### ⚠ Bad Code

```html
<img src="demo.jpg">
```
  
###### ✅ Good Code

 ```html
 <img src="demo.jpg" alt="This is placeholder of the image">
 ``` 
  
 ### Kebab-case names  ![Code Styling](https://img.shields.io/badge/-Code%20Styling-green.svg)
 
 For names, try to use `kebab-case (spinal-case)` and not use `camelCase`, or `snake_case`. Use `snake_case` only when using [BEM](https://en.bem.info/), though if you are using Bootstrap, it’s better to keep consistent and go with `-` as a delimiter.
 
 ###### ⚠ Bad Code

```html
<section class="section_featured_Listing">
  <h1 class="largeTitle">H1 title</h1>
</section>
```
  
###### ✅ Good Code

```html
<section class="section-featured-listing">
  <h1 class="large-title">H1 title</h1>
</section>
```
 
`kebab-case` is more readable then `camelCase` and `snake_case`.
###
**[🔝 ](#table-of-contents)**
###
### 
----
### Meaningful, short names of classes  ![Code Styling](https://img.shields.io/badge/-Code%20Styling-green.svg)

The names of classes should look like `.noun-adjective`, which can be understood by anyone, keep them short

Try to use common names of classes instead of writing content specific names. It makes code more readable

 ###### ⚠ Bad Code

```html
<div class="team-wrapper">
  <button class="large-button-green"></button>
  <p class="greenText-john-smith-description"></p>
  <div class="white-bg"></div>
</div>
```
  
###### ✅ Good Code

```html
<div class="section-team">
  <button class="btn-lg btn-success"></button>
  <p class="text-success"></p>
  <div class="bg-white"></div>
</div>
```
 
### Remove type attributes  ![Code Styling](https://img.shields.io/badge/-Code%20Styling-green.svg)

Don’t write type attributes for stylesheets and script in HTML5. They are not required with HTML5, but are required by W3C standards in HTML4/XHTML.

 ###### ⚠ Bad Code

```html
<link type="text/css" rel="stylesheet" href="../styles.css">
<script type="text/javascript" src="../main.js"></script>
```
  
###### ✅ Good Code

```html
<link rel="stylesheet" href="styles.css">
<script src="app.js"></script>
```

###
**[🔝](#table-of-contents)**
###
###
----
### Use specific classes when necessary  ![Code Styling](https://img.shields.io/badge/-Code%20Styling-green.svg)

Keep the CSS selector more specific and select the elements you need; try not to mention their parents if not necessary. It will allow the code to render faster and remove any managing obstacles in future.

###### ⚠ Bad Code

```html
section aside h1 span {
  margin-left: 25%;
}
```
  
###### ✅ Good Code

```html
.left-offset {
  margin-left: 25%;
}
```

While applying a class to the targeted element may create more code within HTML, it will allow the code to render faster and will remove any managing obstacles.

###
**[🔝](#table-of-contents)**
###
###
----
### Add a class to the parent element  ![Code Styling](https://img.shields.io/badge/-Code%20Styling-green.svg)

If you need to use the same block but with different styling, try to keep the HTML as untouched as possible. Just add one class to the parent element and apply all new stylings to the children of that class in CSS.

###### ⚠ Bad Code

```html
<article>
  <h1>Same section with another styles</h1>
  <p>Lorem ipsum dolor sit amet, lorem sit eget proin id ipsum. </p>
  …
</article>

<article class=”another-article”>
  <h1 class=”other-styling-title”>Same section with another styles</h1>
  <p>Lorem ipsum dolor sit amet, lorem sit eget proin id ipsum. </p>
  …
</article>
```
```css
article {
  padding: 10px 15px;
  h1 {
    font-size: 32px;
    color: #ff0000;
  }
}

.another-article {
  padding-bottom: 30px;
  border-bottom: 4px solid #ccc;
}
h1.other-styling-title {
  font-size: 20px;
}
```
  
###### ✅ Good Code

```html
<article>
  <h1>Same section with another styles</h1>
  <p>Lorem ipsum dolor sit amet, lorem sit eget proin id ipsum. </p>
  … 
</article>

<article class=”other-styling”>
  <h1>Same section with another styles</h1>
  <p>Lorem ipsum dolor sit amet, lorem sit eget proin id ipsum. </p>
  … 
</article>
```
```css
article {
  padding: 10px 15px;
  h1 {
    font-size: 32px;
    color: #ff0000;
  }

  &.other-styling {
    padding-bottom: 30px;
    border-bottom: 4px solid #ccc;
    /* you will have less classes */
    h1 {
      font-size: 20px;
    }
  }
}
```


###
**[🔝](#table-of-contents)**
###
###
----
### Drop units from zero values  ![Code Styling](https://img.shields.io/badge/-Code%20Styling-green.svg)

Adding the unit is unnecessary and provides no additional value. There is no difference between 0px, 0em, 0%, or any other zero-value. The units aren’t important because the value is still zero.

###### ⚠ Bad Code

```html
div {
  margin: 20px 0px;
  letter-spacing: 0%;
  padding: 0px 5px;
}
```
  
###### ✅ Good Code

```html
div {
  margin: 20px 0;
  letter-spacing: 0;
  padding: 0 5px;
}
```

###
**[🔝](#table-of-contents)**
###
###
----
### Use an `hr` tag  ![Code Styling](https://img.shields.io/badge/-Code%20Styling-green.svg)
 
Don’t write `border-bottom` in CSS if you can add an `hr` tag. Use the hr tag instead of writing a new selector and adding border styles in CSS. It makes the code more markup-based, and that’s what we’re going for.

###### ⚠ Bad Code

```html
<p class="border-bottom">I want this section to have a border.</p>
<p>Lorem ipsum</p>
```
```css
.border-bottom {
  border-bottom: 1px solid #000;
}
```
  
###### ✅ Good Code

```html
<p>I want this section to have a border.</p>
<hr>
<p>Lorem ipsum</p>
// If necessary change hr variable in bootstrap
```

###
**[🔝](#table-of-contents)**
###
###
----
### CSS without fixed height and width  ![Code Styling](https://img.shields.io/badge/-Code%20Styling-green.svg)

Try to avoid having fixed height or width in CSS. Heights can be generated by having inner content + paddings and widths can be defined by a grid system (use nested grid if necessary).

###### ⚠ Bad Code

```html
<footer id="footer" class="text-center">
  <h2>Let's Get In Touch!</h2>
  <hr>
  <p>Ready to start your next project with us?</p>
 </footer>
```
```css
#footer {
  height: 130px;
}
```
  
###### ✅ Good Code

```html
<footer id="footer" class="text-center">
  <h2>Let's Get In Touch!</h2>
  <hr>
  <p>Ready to start your next project with us?</p>
</footer>
``` 
```css
#footer {
  padding-top: 23px;
  padding-bottom: 47px;
}
``` 

###
**[🔝](#table-of-contents)**
###
###
## HTML

Moving on to HTML, the priority will be to ensure a robust and easy to maintain front-end.

-----
### Try to have a front-end that is as markup-based as possible  ![HTML](https://img.shields.io/badge/-HTML-e24e30.svg)

Make your front-end code markup-based instead of writing too much CSS.

This will will help search engines and make your code more readable, potentially enhancing search rankings and user experience.


###### ⚠ Bad Code

```html
<div class="main-content">
  <p class="content-title">Main text title</p>
  <img src="http://via.placeholder.com/150x150" alt="example">
  <p class="image-description">Here is image description</p>
</div>
```
  
###### ✅ Good Code

```html
<main>
  <h1>Main text title</h1>
  <figure>
    <img src="http://via.placeholder.com/150x150" alt="example">
    <figcaption>
      Here is image description
    </figcaption>
  </figure>
</main>
```

###
**[🔝](#table-of-contents)**
###
###
----
### Avoid using unnecessary wrappers in HTML  ![HTML](https://img.shields.io/badge/-HTML-e24e30.svg)

Try not to use unnecessary wrapper elements in HTML. Having tons tons of `<div>` and `<span>` elements is a thing of the past. Keeping things granular and linear enables you to achieve minimal code (see next point).

###### ⚠ Bad Code

```html
<section class=”container”>
  <div class=”row”>
    <div class=”col-xs-12”>
      <div class=”inner-wrapper”>
        <span>Unnecessary br tags</span>
      </div>
    </div>
  </div>
</section>
```
  
###### ✅ Good Code

```html
<section class=”container”>
  <p>Unnecessary br tags</p>
</section>
```

###
**[🔝](#table-of-contents)**
###
###
----
### Use atomic classes for styling  ![HTML](https://img.shields.io/badge/-HTML-e24e30.svg)

Do not use any custom colors or font sizes (if the color or font size is not in the framework, just add your atomic classes). Atomic classes are simple, single-purpose units of styling. Much like inline styles, Atomic styles only apply a single style declaration.

###### ⚠ Bad Code

```html
<h1>Without using atomic class</h1>
<p>Paragraph without atomic class</p>
<section>
  <h1> Another h1 text</h1>
  <p>Paragraph inside div without class</p>
</section>
```
```css
h1 {
  color: red;
}
section > h1 {
  color: blue;
}
```
  
###### ✅ Good Code

```html
<h1 class="text-red">Without using atomic class</h1>
<p>Paragraph without atomic class</p>
<section>
  <h1 class="text-blue"> Another h1 text</h1>
  <p>Paragraph inside div without class</p>
</section>
```
```css
.text-red {
  color: red;
}
.text-blue {
  color: blue;
}
```

Try to keep granular and atomic classes, and use them when needed. Your front-end will become more markup-based as a result.

###
**[🔝](#table-of-contents)**
###
###
----
### Make use of semantic elements  ![HTML](https://img.shields.io/badge/-HTML-e24e30.svg)

Using semantics provides a better structure and makes the code and content easier to read.


###### ⚠ Bad Code

```html
<span class="heading"><strong>Welcome</strong></span>
<span>This is unnecessary br tag.</span>
```
  
###### ✅ Good Code

```html
<h1>Welcome</h1>
<p>This is unnecessary br tag.</p>
```

###
**[🔝](#table-of-contents)**
###
###
----
### Use HTML5 tags  ![HTML](https://img.shields.io/badge/-HTML-e24e30.svg)

The new tags give you more expressive freedom and to standardize common elements, which improves the automated processing of documents. Here is a solid list of all elements. I’ve discovered that a lot of developers always use a lot of `<div>` and `<span>`, but first please [check here](https://www.tutorialrepublic.com/html-reference/html5-tags.php) which tags fit logically in your context:
 
###### ⚠ Bad Code

```html
 <div class="article-blue">
  <div class="article-title-red">HTML 4 title</div>
  <div class="content">
    Semantics
    <span class="boldtext">are</span>
    important.
  </div>
</div>
```
  
###### ✅ Good Code

```html
 <article>
  <h1>HTML5 title</h1>
  <p>
    Semantics <strong>are</strong> important.
  </p>
</article>
``` 

Bottom line: Learn and use new elements in HTML5. It’s well worth the effort!

###
**[🔝 ](#table-of-contents)**
###
###
## CSS


When it comes to CSS, it’s hard not to start off with some unoriginal, yet sassy advice:

### A > B selector  ![CSS](https://img.shields.io/badge/-CSS-1572B6.svg)

It’s very helpful to use the `A > B` selector, which applies rules only to direct child(ren), in that case you will not have to reset stylings of all other children which don’t need that styling. For example, it’s very useful when coding nested menus. You will not need to redefine submenu stylings.

###### ⚠ Bad Code

```html
<ul>
  <li>List 1</li>
  <li>List 2</li>
  <li>List 3
    <ul>
      <li>Submenu 1</li>
      <li>Submenu 2</li>
    </ul>
  </li>
</ul>
```
```css
ul li {
  list-style-type: none;
}
li ul li {
  /* redefine to default value */
  list-style-type: disc;
}
```
  
###### ✅ Good Code

```html
<ul>
  <li>List 1</li>
  <li>List 2</li>
  <li>List 3
    <ul>
      <li>Submenu 1</li>
      <li>Submenu 2</li>
    </ul>
  </li>
</ul>
```
```css
ul > li {
  list-style-type: none;
}
```

###
**[🔝](#table-of-contents)**
###
###
----
### Use a CSS preprocessor  ![CSS](https://img.shields.io/badge/-CSS-1572B6.svg)

[Sass](http://sass-lang.com/) is the most mature, stable, and powerful professional grade CSS extension language in the world.

There are two syntaxes available for Sass. The first, known as SCSS (Sassy CSS) and used throughout this reference, is an extension of the syntax of CSS. The second and older syntax, known as the indented syntax (or sometimes just “Sass”), provides a more concise way of writing CSS.

###
**[🔝](#table-of-contents)**
###
###
----
### Use @extend in SASS or group selectors  ![CSS](https://img.shields.io/badge/-CSS-1572B6.svg)

By grouping your selectors, or using `@extend` in SASS, you should help keep your code DRY (Don’t repeat yourself).

###### ⚠ Bad Code

```css
p {
   font-size: 22px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
h1 {
  font-size: 41px;
  color: #000;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```
  
###### ✅ Good Code

```css
.font-smoothing {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

p {
  font-size: 22px;
  @extend .font-smoothing;
}
h1 {
  font-size: 22px;
  @extend .font-smoothing;
}
``` 

###
**[🔝](#table-of-contents)**
###
###
----
### Use rem units  ![CSS](https://img.shields.io/badge/-CSS-1572B6.svg)

Use REMs, instead of pixels for sizes and spacings, for example font sizes it make based on the `font-size` of the root `<html>` element. They also allow you to quickly scale an entire project by changing the root font size (for example at a certain media query/screen size).

You will write less code for responsive views:

###### ⚠ Bad Code

```css
p {
  font-size: 22px;
  padding: 10px;
}

@media (max-width: 767px) {
  p {
    font-size: 16px;
    padding: 5px;
  }
}
```
  
###### ✅ Good Code

```css
html {
  font-size: 14px;
}
@media (max-width: 767px) {
  html {
    font-size: 12px;
  }
}

p {
  font-size: 1.6rem;
  padding: 1rem;
}
``` 

###
**[🔝](#table-of-contents)**
###
###
----
### Before writing a CSS rule think about which element will be affected  ![CSS](https://img.shields.io/badge/-CSS-1572B6.svg)

Always think about which elements will be affected before writing any CSS rule. If your changes won’t be common, then write your rules in a way to affect only a certain element and nothing else.

###### ⚠ Bad Code

```css
/* Commonly used class */
.title {
    color: #008000;
}
```
  
###### ✅ Good Code

```css
/* Specify it not to affect other titles */
.section-blog .title {
    color: #008000;
}
```

###
**[🔝](#table-of-contents)**
###
###
----
### Look for existing CSS rules and variables before writing new ones  ![CSS](https://img.shields.io/badge/-CSS-1572B6.svg)

Always look for existing rules that fit the desired styling, both in custom CSS and in the framework. Only if there is nothing adequate, proceed to writing a new one.

This is particularly important when working with big apps.

###### ⚠ Bad Code

```css
.jumbotron {
  margin-bottom: 20px;
}
```
  
###### ✅ Good Code

```css
// change $jumbotron-padding from _variables.scss
.jumbotron {
  margin-bottom: $jumbotron-padding;
}
```

###
**[🔝](#table-of-contents)**
###
###
----
### Use specific rules  ![CSS](https://img.shields.io/badge/-CSS-1572B6.svg)

If the background has one property, we specify that property, But if it has different background properties, we can give it one declaration.

###### ⚠ Bad Code

```css
.selector {
  background: #fff;
}
```
  
###### ✅ Good Code

```css
.selector {
  /* This way background image will not be overwritten if there is any */
  background-color: #fff;
}
```

###
**[🔝](#table-of-contents)**
###
###
----
### Use shorthand properties and values  ![CSS](https://img.shields.io/badge/-CSS-1572B6.svg)

Do your best to use more shorthand properties and values. Using a shorthand property, you can write concise and, more often than not, much more readable style sheets, saving precious time and energy.


###### ⚠ Bad Code

```css
img {
  margin-top: 5px;
  margin-right: 10px;
  margin-bottom: 25px;
  margin-left: 10px;
}
button {
  padding: 0 0 0 20px;
}
```
  
###### ✅ Good Code

```css
img {
  /* Shorthand style */
  margin: 5px 10px 25px;
}
button {
  /* Don’t play with shorthand too much */
  padding-left: 20px;
}
```

###
**[🔝](#table-of-contents)**
###
###
----
### `em` instead of `px` for line height  ![CSS](https://img.shields.io/badge/-CSS-1572B6.svg)

Use em instead of px for line height, it gives us flexibility in our designs and the ability to scale elements up and down instead of being stuck with fixed sizes. We can use this flexibility to make our designs easier to adjust during development and more responsive as well as allow browser users to control the overall scale of sites for maximum readability.


###### ⚠ Bad Code

```css
p {
  font-size: 12px;
  line-height: 24px;
}
```
  
###### ✅ Good Code

```css
p {
  font-size: 12px;
  line-height: 2em; /* or just line-height: 2; */
}
```

###
**[🔝 ](#table-of-contents)**
###
###
## Bootstrap
  
### Use Bootstrap classes as much as possible  ![Bootstrap](https://img.shields.io/badge/-Bootstrap-7142A8.svg)

While this rule could apply to UI frameworks in general, I am using [Bootstrap](http://getbootstrap.com/) as an example, because it is the world’s most popular front-end component library.

Bootstrap allows you to use a lot of ready classes, making your work easier. Try to use Bootstrap classes as much as possible, to make more HTML-based markup.


###### ⚠ Bad Code

```html
<section class="without-bootstrap">
  <div class="first-column">Lorem ipsum dolor sit amet, ut ius delenit facilisis</div>
  <div class="second-column">Lorem ipsum dolor sit amet, ut ius delenit facilisis</div>
</section>
```
```css
.first-column,
.second-column {
  width: 25%;
  float: left;
  padding-left: 15px;
  padding-right: 15px;
}
```
  
###### ✅ Good Code

```html
<section class="row">
  <div class="col-md-6">Lorem ipsum dolor sit amet, ut ius delenit facilisis</div>
  <div class="col-md-6">Lorem ipsum dolor sit amet, ut ius delenit facilisis</div>
</section>
```

###
**[🔝](#table-of-contents)**
###
###
----
### Use parent item just once in SCSS  ![Bootstrap](https://img.shields.io/badge/-Bootstrap-7142A8.svg)

When you’re using a CSS preprocessor, and planning to write styling for any section, make sure to use the parent item in CSS just once, and include all child elements and media queries inside its brackets. This will allow you to find and modify the main parent element easily in one place when making changes in future.

###### ⚠ Bad Code

```css
.section-parent-class {
  position: relative;
  h2 {
      color: #ff0;
    }
  header {
    margin: 2rem 1rem;
  }
}

@media (max-width: 767px) {
  .section-parent-class {
    footer {
      padding: .5rem;
    }
  }
}
```
  
###### ✅ Good Code

```css
.section-parent-class {
  position: relative;
  h2 {
    color: #ff0;
  }
  header {
    margin: 2rem 1rem;
  }
  
  footer {
    @media (max-width: 767px) {
      padding: .5rem;
    }
  }
}
```

###
**[🔝](#table-of-contents)**
###
###
----
### Customize your framework properly  ![Bootstrap](https://img.shields.io/badge/-Bootstrap-7142A8.svg)

Bootstrap relies on the [variables.scss](https://github.com/twbs/bootstrap/blob/v4-dev/scss/_variables.scss) file, which allows you to easily configure and customize your front-end without writing a single line of code. Otherwise, if you are going to manually write all the customizations on your own, you’d be better not to use a framework at all.

Some developers avoid changing variables.scss, thinking they will still be able to upgrade Bootstrap to a new version without much hassle, but it can be a tedious task. Even minor updates require developers to read the changelog, go through all markup and CSS, and migrate to the new version manually.

###### ⚠ Bad Code

```css
.navbar {
  padding: 20px 10px;
}
.carousel-indicators {
  li {
    width: 6px;
    height: 6px;
    margin-right: 3px;
    margin-left: 3px;
  }
}
```
  
###### ✅ Good Code

```html
$navbar-padding-y:      ($spacer / 2) !default;
$navbar-padding-x:      $spacer !default;

$carousel-indicator-width:       30px !default;
$carousel-indicator-height:      3px !default;
$carousel-indicator-spacer:      3px !default;
```

###
**[🔝](#table-of-contents)**
###
###
----
### Don’t overwrite `.container` width  ![Bootstrap](https://img.shields.io/badge/-Bootstrap-7142A8.svg)

Try to not overwrite `.container`’s width. Try using a grid system instead, or just change the container width in `_variables.scss`. If you need to decrease its width, just use max-width instead of width. In that case, `.container` from Bootstrap will stay untouched in responsive views.

###### ⚠ Bad Code

```css
.container {
  @media (min-width: $screen-lg-min) {
      width: 1300px;
  }
}
```
  
###### ✅ Good Code

```html
// change $container-lg from _variables.scss
.container {
  @media (min-width: $screen-lg-min) {
    width: $container-lg;
  }
}
```

###
**[🔝](#table-of-contents)**
###
###
----
### Use Bootstrap 4 classes and write less CSS  ![Bootstrap](https://img.shields.io/badge/-Bootstrap-7142A8.svg)

Start using Bootstrap 4, even though it’s in beta. It includes many new classes which will help you create layouts faster, especially Flexbox and spacers

###### ⚠ Bad Code

```html
<div class="flex-ex">
  <div>Flex item 1</div>
  <div>Flex item 2</div>
  <div>Flex item 3</div>
</div>
<div class="flex-ex flex-reverse">
  <div>Flex item 1</div>
  <div>Flex item 2</div>
  <div>Flex item 3</div>
</div>
```
```css
.flex-ex {
  display: flex;
  > div {
    padding: 2px;
  }
  &.flex-reverse {
    flex-direction: row-reverse;
  }
  li {
   list-style: none;
    padding: .5rem;
  }
}
```
  
###### ✅ Good Code

```html
 <ul class="list-unstyled list-inline d-flex flex-row">
  <li class="p-2">Flex item 1</li>
  <li class="p-2">Flex item 2</li>
  <li class="p-2">Flex item 3</li>
</ul>
<ul class="list-unstyled list-inline d-flex flex-row-reverse">
  <li class="p-2">Flex item 1</li>
  <li class="p-2">Flex item 2</li>
  <li class="p-2">Flex item 3</li>
</ul>
```

Now we can assign classes to an element to remove all borders or some borders.

###### ⚠ Bad Code

```html
<div class="border-example2 py-5">
  <span class="border0"></span>
  <span class="border-top0"></span>
  <span class="border-right0"></span>
  <span class="border-bottom0"></span>
  <span class="border-left0"></span>
</div>
```
```css
.border-example2 {
  > span {
    width: 100px;
    height: 100px;
    display: inline-block;
    margin: .50rem;
    background-color: #e1e1e1;
    border: 1px solid;
      &.border0 {
        border: none;
      }
      &.border-top0 {
        border-top: none;
      }
      &.border-right0 {
        border-right: none;
      }
      &.border-bottom0 {
        border-bottom: none;
      }
      &.border-left0 {
        border-left: none;
      }
    }
}
```

###### ✅ Good Code

```html
<div class="border-example py-5">
  <span class="d-inline-block m-2 border-0"></span>
  <span class="d-inline-block m-2 border-top-0"></span>
  <span class="d-inline-block m-2 border-right-0"></span>
  <span class="d-inline-block m-2 border-bottom-0"></span>
  <span class="d-inline-block m-2 border-left-0"></span>
</div>
```
```css
.border-example {
  > span {
    width: 100px;
    height: 100px;
    background-color: #e1e1e1;
    border: 1px solid;
  }
}
```

###
**[🔝](#table-of-contents)**
###
###
----
### Remove `.col-md-X` and `.col-lg-X` if `.col-sm-X` has same value for X  ![Bootstrap](https://img.shields.io/badge/-Bootstrap-7142A8.svg)

Don’t write `.col-md-X` and `.col-lg-X` if .col-sm-X has same value for X. For example, there is no need to write `.col-lg-10` because when we write `.col-md-10`, we automatically include `.col-lg-10` in it

###### ⚠ Bad Code

```html
<ul class="press-list list-inline row">
  <li class="col-lg-4 col-md-4 col-sm-4 col-xs-6"><a href="#"><img class="img-fluid" src="assets/images/press/press-1.png" alt=""></a></li>
  <li class="col-lg-4 col-md-4 col-sm-4 col-xs-6"><a href="#"><img class="img-fluid" src="assets/images/press/press-2.png" alt=""></a></li>
</ul>
```

###### ✅ Good Code

```html
<ul class="press-list list-inline row">
  <li class="col-md-4 col-xs-6"><a href="#"><img class="img-fluid" src="assets/images/press/press-1.png" alt=""></a></li>
  <li class="col-md-4 col-xs-6"><a href="#"><img class="img-fluid" src="assets/images/press/press-2.png" alt=""></a></li>
</ul>
```

###
**[🔝](#table-of-contents)**
###
###
----
### Don’t use `.col-xs-12`  ![Bootstrap](https://img.shields.io/badge/-Bootstrap-7142A8.svg)

Don’t use `.col-xs-12` because if no .col-xs-X is assigned, then it will be `.col-xs-12` by default.

###### ⚠ Bad Code

```html
<section id="services">
  <div class="container">
    <div class="row">
      <div class="col-lg-12 text-center">
        <h2>Services</h2>
        <h3 class="text-muted">Lorem ipsum dolor sit amet consectetur.</h3>
      </div>
    </div>
    <div class="row text-center">
      <div class="col-md-6 col-xs-12">
        <h4>E-Commerce</h4>
        <p class="text-muted">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
      </div>
    </div>
  </div>
</section> 
```

###### ✅ Good Code

```html
<section id="section-services" class="text-center">
  <div class="container">
    <h2>Services</h2>
    <h3 class="text-muted">Lorem ipsum dolor sit amet consectetur.</h3>
    <div class="row">
      <div class="col-md-6">
        <h4>E-Commerce</h4>
        <p class="text-muted">Lorem ipsum dolor sit amet, consectetur adipisicing.</p>
      </div>
    </div>
  </div>
</section> 
```

###
**[🔝](#table-of-contents)**
###
###
----
### Don’t use `reset.css`; use `normalize.css` instead

If you are using Bootstrap, then `normalize.css` is already included there, no need to include it twice.

----
### Follow guidelines, even if they’re not a best practice

For the sake of consistency, it’s better to always follow the rules and guidelines you started with (whether they’re about naming, code style, or file structure)

----
### Wrapping Up

I hope you have been able to take away something helpful and that you will think more about writing minimal HTML and CSS code with best practices.

For big companies, it’s quite difficult to maintain big applications when there is messy code. And of course, big companies have the money to pay for good quality. If you follow clean coding principles, you’ll improve your chances of landing a good job. It’s also worth bringing up the freelance aspect: Professionals juggling multiple projects and clients must deliver clean code that can be passed on to other developers in no time.

I hope to expand to more advanced topics in future posts, as I intend to talk about automating the coding process, using Gulp/Grunt tasks, Linters, Editor plugins, tools that generate code, AI tools that write code instead of you, and other related topics.

I hope this has been an interesting and informative read. Good luck in your coding endeavors.
