
# HTML
Most of the guidelines mentioned here adhere to Google Coding standards for HTML and CSS. Wherever needed we have modified the rules to suit our needs. This document contains generic CSS guideline as well as some specific SCSS guidelines.

## Document Type
Use Html5
```html
<!DOCTYPE html>.
```
## Language
Always define which language the page is written in.
```html
<html lang="en">
```
## Encoding
Always define the character encoding. The encoding should be defined as early as possible. Make sure your editor uses UTF-8 as character encoding, without a byte order mark (UTF-8, no BOM). Do not specify the encoding of style sheets as these assume UTF-8
```html
<meta charset="utf-8">
```
## Protocol
Omit the protocol portion (http:, https:) from URLs pointing to images and other media files, style sheets, and scripts unless the respective files are not available over both protocols.
Omitting the protocol—which makes the URL relative—prevents mixed content issues and results in minor file size savings.

```html
<!-- bad -->
<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>
<!-- good -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```
## IE Edge case
Use IE edge mode in meta tag
```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```
If this is note used, IE can use compatibility mode and render the page using an older version of IE such as IE7. Place this immediately after <title> tag

## Semantics
Use html tag which are semantic to its purpose
```html
<!-- bad -->
<div id="header"></div>
<!-- good -->
<header></header>
```
## Accessibility
Use alt tag to specify the purpose of media files (image, audio, video) so that on browsers (or screen readers) where the media does not play or takes time to render, the user can figure out the purpose of the content:
```html
<!-- bad -->
<img src="spreadsheet.png">
<!-- good -->
<img src="spreadsheet.png" alt="Spreadsheet screenshot.">
```

## Spacing
Use space instead tabs. Indent using 4 spaces.
```html
<!-- bad -->
<ul>
  <li>Fantastic</li>
  <li>Great</li>
</ul>
<!-- good -->
<ul>
    <li>Fantastic
    <li>Great
</ul>
```
Use a line limit of 120 characters.

## Naming convention
Use only lowercase for both HTML and CSS.
All code has to be lowercase: This applies to HTML element names, attributes, attribute values (unless text/CDATA), CSS selectors, properties, and property values (with the exception of strings).

```html
<!-- bad -->
<A HREF="/">Home</A>
color: #E5E5E5;

<!-- good -->
<img src="google.png" alt="Google">
color: #e5e5e5;
```
Use hyphen for user-defined tags and attributes
```html
tag-name-like-this
attribute-name-like-this
```
Prefix custom attribute with “data-“
```html
data-my-attr
```
d used should be unique across the page. Id, if present, should be the first attribute of an element followed by class (if present)
```html
<!-- bad -->
<input maxlength="20" id="email" type="email" class="login-box">

<!-- good -->
<input id="email" class="login-box" maxlength="20" type="email">
```

## Trailing Whitespaces
Remove trailing white spaces.
Trailing white spaces are unnecessary and can complicate diffs.
```html
<!-- bad -->
<p>No, thank you. </p>
<!-- good -->
<p>Yes please.</p>

```
## General Formatting
Paragraphs of text should always be placed in a `<p>` tag. Never use multiple `<br>` tags.
Items in list form should always be in `<ul>`, `<ol>`, or `<dl>`. Never use a set of `<div>` or `<p>`.
Every form input that has text attached should utilize a `<label>` tag. Especially radio or checkbox elements.
Even though quotes around attributes is optional, always put quotes around attributes for readability. 
Avoid trailing slashes in self-closing elements. For example,` <br>`, `<hr>`, `<img>`, and `<input>`.
Don’t set tabindex manually—rely on the browser to set the order. 

## Lean markup
Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML. For example:
```html
<!-- bad -->
<span class="avatar">
  <img src="...">
</span>
<!-- good -->
<img class="avatar" src="...">
```
## Tables
Make use of `<thead>`, `<tfoot>`, `<tbody>`, and `<th>` tags (and scope attribute) when appropriate. (Note: `<tfoot>` goes above `<tbody>` for speed reasons. You want the browser to load the footer before a table full of data.)
```html
<table summary="This is a chart of invoices for 2011.">
  <thead>
    <tr>
      <th scope="col">Table header 1</th>
      <th scope="col">Table header 2</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <td>Table footer 1</td>
      <td>Table footer 2</td>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>Table data 1</td>
      <td>Table data 2</td>
    </tr>
  </tbody>
</table>

```

## Multimedia formats
Preferably use multiple source types for multimedia files like video and audio. Every browser supports a different audio/video codec. e.g. WebM video format is supported in FireFox but not in Safari. So to cater to all browsers use the following:
```html
<video controls>
    <source src="somevideo.webm" type="video/webm">
    <source src="somevideo.mp4" type="video/mp4">
    I'm sorry; your browser doesn't support HTML5 video in WebM with VP8 or MP4 with H.264.
</video>
```
For more info on supported media formats: https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats 

## Separation of Concern
Keep structure (HTML) separate from presentation (Styling) separate from behavior (Script). 
Avoid inline styling and scripting in HTML tag.
```html
<!-- bad -->
<div style="background-color:#000" onclick="alert('I am clicked!')"></div>

<!-- good -->
<style>
.hightlight {
    background-color: #000;
}
</style>

<div class="highlight"></div>
<script>
    $('.highlight').click(function(){
        alert('I am clicked');
    });
<script>
```
CSS, HTML, JS can be kept in the same file if it’s a component (like Web Components). Otherwise keep them in separate files so that they can be minimized. 

## Type attribute
Omit type attributes for style sheets and scripts.
Do not use type attributes for style sheets (unless not using CSS) and scripts (unless not using JavaScript).
Specifying type attributes in these contexts is not necessary as HTML5 implies text/css and text/javascript as defaults. This can be safely done even for older browsers.

```html
<!-- bad -->
<link rel="stylesheet" href="//www.google.com/css/maia.css" type="text/css">
 <!-- good -->
<link rel="stylesheet" href="//www.google.com/css/maia.css">

 <!-- bad -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"
  type="text/javascript"></script>
 <!-- good -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

## Quotation mark

When quoting attributes values, use double quotation marks.
```html
<!-- bad -->
<a class='maia-button maia-button-secondary'>Sign in</a>
 <!-- good -->
<a class="maia-button maia-button-secondary">Sign in</a>
```
##  Markup validation Tools
[w3 Validator](https://validator.w3.org/)
[csslint](http://csslint.net/)
## Resources
[CodeGuide](https://codeguide.co/)
[Google HTML & CSS Guide](https://google.github.io/styleguide/htmlcssguide.html)
[w3school](https://www.w3schools.com/html/html5_syntax.asp)
[HTML Best Practices](https://github.com/hail2u/html-best-practices)