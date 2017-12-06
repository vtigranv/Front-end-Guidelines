# Front-end Guidelines

## Introduction
During my 15 years of experience in web development, I’ve worked with various companies, from enterprise-level to startups, and I’ve worked with many, many fellow software engineers along the way. One of the most common and important problems I’ve came across in my projects has been failure to write clean and easy-to-understand code. 
Even the best developers from top-notch companies don’t always follow best practices and write code which can be cleaned and optimized.

## Problems and consequences of messy and dirty code
> “Source code is akin to financial debt. Suppose you want to buy a house to live in. Most people don’t have the financial wherewithal to pay cash for a house, so you take out a mortgage instead. But the mortgage itself is not a great thing to have. It’s a liability. You have to pay interest on your debt every month. You always want your mortgage to be as small as possible while still allowing you to buy a house that meets your needs. But if you don’t do some careful thinking about the terms and implications of your mortgage before you buy a house, you can wind up in a load of trouble. It’s possible to end up underwater in a situation where your debt is actually bigger than your house is worth.

> So too in web development. The code has ongoing costs. You have to understand it, you have to maintain it, you have to adapt it to new goals over time. The more code you have, the larger those ongoing costs will be. It’s in our best interest to have as little source code as possible while still being able to accomplish our business goals.”
 
 
Quoted from an old but still relevant blog post: https://blogs.msdn.microsoft.com/elee/2009/03/11/source-code-is-a-liability-not-an-asset/


## Table of Contents

  1. [File structure](#file-structure)
  1. [Code validation](#code-validation)



## File Structure

If you are going to develop a big app, then you need to take care of the file structure. It can, or rather should, look like this:

![Good example of file structure in SCSS](https://raw.githubusercontent.com/vtigranv/Front-end-Guidelines/master/assets/file-structure.png)

## Code validation

Try to always check your code with [HTML](https://validator.w3.org/) and [CSS](https://jigsaw.w3.org/css-validator/) validators

###### Bad Code

  ```html
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
  ```
  ```css
  p {
    font: 400 inherit/1.125 serif;
  }
  ```

###### Good Code

  ```html
  <figure>
    <img src="demo.jpg" alt="">
    <!-- figcaption should be child of element figure element, not div -->
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
