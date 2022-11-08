# CSS
## Spacing
Use space instead of tab. Use 4 spaces for indentation. Spaces are the only way to guarantee code renders the same in any person’s environment.\
Put spaces after : in property declarations.\
Put spaces before { in rule declarations.\
Put line breaks between rulesets.\
When grouping selectors, keep individual selectors to a single line.\
Place closing braces of declaration blocks on a new line.
```html
<!-- bad -->
.add-section {
  margin: 20px;
}
input:focus, textarea:focus, select:focus{
  border-top-width: 2px; border-bottom-width:2px; }
<!-- good -->
.add-section {
    margin: 20px;
}

input:focus, 
textarea:focus, 
select:focus {
    border-top-width: 2px;
    border-bottom-width: 2px;
}
```

## Comments
Use // for comment blocks (instead of /* */).
```html
<!-- bad -->
/* Do not comment like this */
.add-section {
    margin: 20px;
}
<!-- good -->
// Some comment here
.add-section {
    margin: 20px;
}
```

## Zero Values
Avoid specifying units for zero values
```html
<!-- bad -->
.add-section {
    margin: 0px;
}
<!-- good -->
.add-section {
    margin: 0;
}
```

Omit leading “0”s in values.\
Do not use put 0s in front of values or lengths between -1 and 1.
```html
<!-- bad -->
font-size: 0.8em;
<!-- good -->
font-size: .8em;
```
  
## Short hands
Use short hands in places where you need to specify all the values explicitly
```html
<!-- bad -->
.add-section {
    margin-top: 10px;
    margin-right: 10px;
    margin-bottom: 10px;
    margin-left: 10px;
    border-width: 10px;
    border-color: #000;
    border-style: solid;
}
<!-- good -->
.add-section {
    margin: 10px 20px 10px 30px;
    border: 20px #000 solid;
}
```
Avoid Short hands if you do not have explicit values for all available values.

  
## Specificity
Use classes instead of id as selector in css
```html
<!-- bad -->
#the_specific_section {
    margin: 10px 20px 10px 30px;
    border: 20px #000 solid;
}
<!-- good -->
.section {
    margin: 10px 20px 10px 30px;
    border: 20px #000 solid;
}
```
Use id only if the style is to be applied to a single element. If you have id in css, make sure not to have more than one # in a selector. 
```html
<!-- bad -->
#header .search #quicksearch { ... }
``` 
If using scss-lint to validate the file, use disabled comment to ignore rule to not use id in css. Remember to enable it after the block. IdSelector checks for no usage of id in css file, SelectorFormat checks for hyphenated selectors by default which is needed in class names but not id.
```html
<!-- good -->
// scss-lint:disable IdSelector SelectorFormat
#template_admin_pages {
    height: 100%;
    width: 100%;
}
// scss-lint:enable IdSelector SelectorFormat
```
The class names disabled, mousedown, danger, hover, selected, and active should always be namespaced by a class.
```html
<!-- bad -->
disabled { ... }
<!-- good -->
button.disabled { ... }
```

Avoid qualifying ID and class names with type selectors.\
Unless necessary (for example with helper classes), do not use element names in conjunction with IDs or classes.\
Avoiding unnecessary ancestor selectors is useful for performance reasons.
```html
<!-- bad -->
ul#example {}
div.error {}
<!-- good -->
#example {}
.error {}
```

## Naming convention
Use ID and class names that are as short as possible but as long as necessary.\
E.g. #nav not #navigation, .author not .atr

Do not concatenate words and abbreviations in selectors by any characters (including none at all) other than hyphens, in order to improve understanding and scannability.\
E.g. .demo-image not .demoimage or .demo_image
```html
<!-- good -->
class-names-like-this
ids_like_this
mixin-names-like-this
```
Use class names for what the element is for and not how it looks like
```html
<!-- bad -->
.red-box { 
    color: #f00;
}
 <!-- good -->
.error {
    color: #f00;
}
```
## Units
Unit-less line-height is preferred because it does not inherit a percentage value of its parent element, but instead is based on a multiplier of the font-size. \
Avoid use of em. Use rem instead with a fall back of pixel unit
```html
<!-- good -->
font-size: 32px; 
font-size: 2rem;
```
  
## Declaration order
Put declarations in alphabetical order in order to achieve consistent code in a way that is easy to remember and maintain.\
Ignore vendor-specific prefixes for sorting purposes. However, multiple vendor-specific prefixes for a certain CSS property should be kept sorted (e.g. -moz prefix comes before -webkit).
```html
<!-- good -->
background: fuchsia;
border: 1px solid;
-moz-border-radius: 4px;
-webkit-border-radius: 4px;
border-radius: 4px;
color: black;
text-align: center;
text-indent: 2em;
```
  
## Semicolon
Use semicolon after every declaration
```html
<!-- bad -->
.test {
  display: block;
  height: 100px
}
 <!-- good -->
.test {
  display: block;
  height: 100px;
}
```
  
## Quotation marks
Use single ('') rather than double ("") quotation marks for attribute selectors or property values. Do not use quotation marks in URI values (url()).
```html
<!-- bad -->
@import url("//www.google.com/css/maia.css");
html {
  font-family: "open sans", arial, sans-serif;
}
<!-- good --> 
@import url(//www.google.com/css/maia.css);
html {
  font-family: 'open sans', arial, sans-serif;
}
```
# SCSS
## Selector Hierarchy
Use selector hierarchy instead of flat structure. This created better readability and is more maintainable
```html
<!-- bad -->
.ui-widget-content {
    background: $secondary-theme-color-2;
    color: $primary-theme-text-on-color-2;
}

.ui-widget-content a {
    color: $primary-theme-text-on-color-2;
}
<!-- good -->
.ui-widget-content {
    background: $secondary-theme-color-2;
    color: $primary-theme-text-on-color-2;
    a {
        color: $primary-theme-text-on-color-2;
    }
}
```
Avoid nesting more than 4 levels. Also break a block into multiple blocks it exceeds more than 50 lines. A long block that does not fit the screen height can nullify the understandability advantage that nesting of rulesets brings in.

  
## Color
Use hex color codes #000 instead of color names. SCSS’ rgba() function is overloaded to accept hex colors as a param, e.g., rgba(#000, .5)
```html
<!-- bad -->
.my-class {
    color: orange;
}
<!-- good -->
.my-class {
    color: #ffa500;
}
```
Use 3 character hexadecimal notation where possible.
For color values that permit it, 3 character hexadecimal notation is shorter and more succinct.
```html
<!-- bad -->
color: #eebbcc;
 <!-- good -->
color: #ebc;
```
  
## Use SCSS variables 
Using variables enables consistent styling and more maintainable code.\
It also allows easy switching of themes.\
Use a separate file to store variables and import it in all scss files as needed.
_theme.scss:
```html
$font-stack: "Segoe UI", Helvetica;
$light-font-weight: 300;
$semi-light-font-weight: 300;
$normal-font-weight: 400;
$heavy-font-weight: 500;

// primary theme 
$primary-theme-color-1: #0082c8;
$primary-theme-color-2: #fff;
$primary-theme-text-on-color-1: #fff;
$primary-theme-text-on-color-2: #222;
...
```
neonlite.scss:
```html
@import 'theme';

button {
    border: solid 1px $primary-theme-border-color;
    color: $primary-theme-color-1;
}
```
Add all theme related properties as variables in _theme.scss file
```html
font
color
background-color
```
  
## Mixins
Use mixins for commonly used styles like font size
```html
@mixin fontSize($size) {
    font-size: $size; //Fallback in px
    font-size: #{$size/16px}rem;
}

.page-title {
    font-weight: $light-font-weight;
    @include fontSize(30px);
}
```
any time you'd use a mixin with no parameter, an extend will be more efficient
```html
.foo {
    color: #f00;
}
.bar {
    @extend .foo;
}
```
This outputs to following css:
```html
.foo, .bar {
    color: #f00;
}

@mixin stuff {
    color: #f00;
}
.foo {
    @include stuff;
} 
.bar {
    @include stuff;
}
```
This will get those styles into both selectors. This is often easier to understand and has less "gotchas," so is more common to see. Note that the output moves the styles into both places:
```html
.foo {
    color: red;
}
.bar {
    color: red;
}
```
## Indentation
Avoid indentation of more than 4 levels 
```html
<!-- bad -->
.class-1 {
    &.class-2 {
        &.class-3 {
            &.class-4 {
                &.class-5 {
                   ...
                }
           }
        }
    }
}

<!-- good -->
.class-1 {
    &.class-2 {
        &.class-3 {
        }
    }
}
```
  
## Vendor specific properties
Do not manually add vendor specific settings in SCSS. Instead set Autoprefixer to true in Web Essentials to auto create vendor specific settings
```html
<!-- bad -->
* {
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}
<!-- good -->
* {
    box-sizing: border-box;
}
```
