# HTML
## Terminology
> [Intro to HTML From MDN](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Introduction)

* Tags
* Attributes
  * = Name + Value
  * There are boolean attributes that only have one value.
  ```html
  <input required="required">
  <input required="">
  <input required>
  ```

* **Named character refernces** - For characters that have special meaning in HTML
  * `&gt;` = `>`
  * `&lt;` = `<`
  * `&amp;` = `&` (ampersand)
  * `&quot;` = `"`
* Doctype
  * tells the browser how to interpret the HTML and CSS according to W3C standards
  * `<!DOCTYPE html>` for HTML5

## Basic structure
> [basic structure](http://www.sitepoint.com/web-foundations/basic-structure-of-a-web-page/#page-structure__fig-doc-tree)

```HTML
<!DOCTYPE html>

<html>
	<head> <!-- metadata -->
		<title>document's title</title> <!-- appears in the browser's title bar & search result 
        <!--
        Other optional tags:
          * base
          * link
          * meta
          * object
          * script
          * style
        -->
	</head>

<body>

</body>
</html>

```

## Block-level elements
> [Block-level elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)

* Block-level vs. inline
  * Formatting (begin on a new line)
  * [Content categories](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Content_categories) in HTML5
* HTML5 adds `<header>`, `<footer>`, `section`... block-level elements which roughly correspond to the category of *flow content* in HTML5.

## Element
* `table` ([ref](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table))
* [HTML forms guide](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Forms)