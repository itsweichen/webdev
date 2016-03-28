# CSS

> [Getting started with CSS](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_started)

## Intro
How it works
* The browser converts the markup language and the CSS into the *DOM*.

*Cascading* Style Sheets
* Browser's default styles
* Styles specified by the user
* Styles linked to the document by the author
  * external
  * def at the begining: used for styles only used on that page
  * on an element in the body: can be used for testing


## [Selectors](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_Started/Selectors)
```
selector { 
  //declaration inside
  property: value;
}
```
* Class selectors
* ID selectors


* Attribute selectors
  * use square brackets and put attr name inside
  * optionally followed by a matching operator and a value
  * `i` indicates it's case-insensitive (not fully supported by browsers)

```
[diabled] [type='button']
[class~=key]
[lang|=es]
[title*="example"]
a[href^="https://"]
img[src$=".png"]
```
> More on [here](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors).

* Pseudo-classes selectors
  * `:hover`, `:focus`, `:nth-child`, `:checked`, etc.

