# Getting started with CSS

## Section 1.1: External Stylesheet

An external CSS stylesheet can be applied to any number of HTML documents by placing a <link> element in each HTML document.

The attribute rel of the **<link>** tag has to be set to _"stylesheet"_, and the href attribute to the relative or absolute path to the stylesheet. While using relative URL paths is generally considered good practice, absolute paths can be used, too. In HTML5 the type attribute [can be omitted](https://html.spec.whatwg.org/multipage/semantics.html#the-link-element).

It is recommended that the **<link>** tag be placed in the HTML file's **<head>** tag so that the styles are loaded before the elements they style. Otherwise, _**users will see a flash of unstyled content**_.

Example

**hello-world.html**

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <link rel="stylesheet" type="text/css" href="style.css">
  </head>
  <body>
    <h1>Hello world!</h1>
    <p>I ♥ CSS</p>
  </body>
</html>
```

**style.css**

```css
h1 {
  color: green;
  text-decoration: underline;
}
p {
  font-size: 25px;
  font-family: 'Trebuchet MS', sans-serif;
}
```

Make sure you include the correct path to your CSS file in the href. If the CSS file is in the same folder as your HTML file then no path is required (like the example above) but if it's saved in a folder, then specify it like this href=**"foldername/style.css"**.

```html
<link rel="stylesheet" type="text/css" href="foldername/style.css">
```

External stylesheets are considered the best way to handle your CSS. There's a very simple reason for this: when
you're managing a site of, say, 100 pages, all controlled by a single stylesheet, and you want to change your link colors from blue to green, it's a lot easier to make the change in your CSS file and let the changes "cascade" throughout all 100 pages than it is to go into 100 separate pages and make the same change 100 times. Again, if you want to completely change the look of your website, you only need to update this one file.

You can load as many CSS files in your HTML page as needed.

```html
<link rel="stylesheet" type="text/css" href="main.css">
<link rel="stylesheet" type="text/css" href="override.css">
```

CSS rules are applied with some basic rules, and order does matter. For example, if you have a main.css file with some code in it:

```css
p.green { color: #00FF00; }
```

All your paragraphs with the 'green' class will be written in light green, but you can override this with another .css file just by including it after main.css. You can have override.css with the following code follow main.css, for example:

```css
p.green { color: #006600; }
```

Now all your paragraphs with the 'green' class will be written in darker green rather than light green.

Other principles apply, such as the '!important' rule, specificity, and inheritance.

When someone first visits your website, their browser downloads the HTML of the current page plus the linked CSS file. Then when they navigate to another page, their browser only needs to download the HTML of that page; the CSS file is cached, so it does not need to be downloaded again. Since browsers cache the external stylesheet, your pages load faster.

## Section 1.2: Internal Styles

CSS enclosed in **<style></style>** tags within an HTML document functions like an external stylesheet, except that it lives in the HTML document it styles instead of in a separate file, and therefore can only be applied to the document in which it lives. Note that this element must be inside the <head> element for HTML validation (though it will work in all current browsers if placed in body).

```html
<head>
    <style>
        h1 {
            color: green;
            text-decoration: underline;
        }
        p{
            font-size: 25px;
            font-family: 'Trebuchet MS', sans-serif;
        }
    </style>
</head>
<body>
  <h1>Hello world!</h1>
  <p>I ♥ CSS</p>
</body>
```

## Section 1.3: CSS @import rule (one of CSS at-rule)

The @import CSS at-rule is used to import style rules from other style sheets. These rules must precede all other types of rules, except @charset rules; as it is not a nested statement, @import cannot be used inside conditional group at-rules. [@import](https://developer.mozilla.org/en/docs/Web/CSS/@import).

### How to use @import

You can use @import rule in following ways:

#### A. With internal style tag

```css
<style>
 @import url('/css/styles.css');
</style>
```

#### B. With external stylesheet

The following line imports a CSS file named additional-styles.css in the root directory into the CSS file in which it appears:

```css
@import '/additional-styles.css';
```

Importing external CSS is also possible. A common use case are font files.

```css
@import 'https://fonts.googleapis.com/css?family=Lato';
```

An optional second argument to @import rule is a list of media queries:

```css
@import '/print-styles.css' print;
@import url('landscape.css') screen and (orientation:landscape);
```

## Section 1.4: Inline Styles

Use inline styles to apply styling to a specific element. Note that this is **not** optimal. Placing style rules in a **<style>** tag or external CSS file is encouraged in order to maintain a distinction between content and presentation.

Inline styles override any CSS in a **<style>** tag or external style sheet. While this can be useful in some circumstances, this fact more often than not reduces a project's maintainability.

The styles in the following example apply directly to the elements to which they are attached.

```css
<h1 style="color: green; text-decoration: underline;">Hello world!</h1>
<p style="font-size: 25px; font-family: 'Trebuchet MS';">I ♥ CSS</p>
```

Inline styles are generally the safest way to ensure rendering compatibility across various email clients, programs and devices, but can be time-consuming to write and a bit challenging to manage.

## Section 1.5: Changing CSS with JavaScript

### Pure JavaScript

It's possible to add, remove or change CSS property values with JavaScript through an element's style property.

```js
let el = document.getElementById("element");
el.style.opacity = 0.5;
el.style.fontFamily = 'sans-serif';
```

Note that style properties are named in lower camel case style. In the example you see that the css property font- family becomes fontFamily in javascript.

As an alternative to working directly on elements, you can create a <style> or <link> element in JavaScript and append it to the <body> or <head> of the HTML document.

## Section 1.6: Styling Lists with CSS

There are three different properties for styling list-items: list-style-type, list-style-image, and list-style- position, which should be declared in that order. The default values are disc, outside, and none, respectively. Each property can be declared separately, or using the list-style shorthand property.

**list-style-type** defines the shape or type of bullet point used for each list-item. 

Some of the acceptable values for list-style-type:

* disc
* circle
* square
* decimal
* lower-roman
* upper-roman
* none

(For an exhaustive list, see the [W3C specification wiki](https://www.w3.org/wiki/CSS/Properties/list-style-type))

To use square bullet points for each list-item, for example, you would use the following property-value pair:

```css
li {
  list-style-type: square;
}
```

The **list-style-image** property determines whether the list-item icon is set with an image, and accepts a value of none or a URL that points to an image.

```css
li {
  list-style-image: url(images/bullet.png);
}
```

The **list-style-position** property defines where to position the list-item marker, and it accepts one of two values: "inside" or "outside".

```css
li {
 list-style-position: inside;
}
```

---------------

# Structure and Formatting of a CSS Rule

## Section 2.1: Property Lists

Some properties can take multiple values, collectively known as a **property list**.

```css
/* Two values in this property list */
span {
  text-shadow: yellow 0 0 3px, green 4px 4px 10px;
}
/* Alternate Formatting */
span {
  text-shadow:
    yellow 0 0 3px,
    green 4px 4px 10px;
}

```

## Section 2.2: Multiple Selectors

When you group CSS selectors, you apply the same styles to several different elements without repeating the styles in your style sheet. Use a comma to separate multiple grouped selectors.

```css
div, p { color: blue }
```

So the blue color applies to all **<div>** elements and all **<p>** elements. Without the comma only **<p>** elements that are
a child of a **<div>** would be red.

This also applies to all types of selectors.

```css
p, .blue, #first, div span{ color : blue }
```

This rule applies to:

  * <p>
  * elements of the blue class
  * element with the ID first
  * every <span> inside of a <div>

## Section 2.3: Rules, Selectors, and Declaration Blocks

A CSS **rule** consists of a **selector** (e.g. h1) and **declaration block** ({}).

```css
h1 {}
```

-----

# Comments

## Section 3.1: Single Line

```css
/* This is a CSS comment */
  div {
    color: red; /* This is a CSS comment */
  }
```

## Section 3.2: Multiple Line 

```css
/*
This
    is
    a
    CSS
    comment
*/
  div {
    color: red;
  }
```
-----

# Selectors

CSS selectors identify specific HTML elements as targets for CSS styles. This topic covers how CSS selectors target HTML elements. Selectors use a wide range of over 50 selection methods offered by the CSS language, including elements, classes, IDs, pseudo-elements and pseudo-classes, and patterns.

## Section 4.1: Basic selectors

| Selector | Description |
|----------|-------------|
| * | Universal selector (all elements) |
| div | Tag selector (all <div> elements) |
| .blue | Class selector (all elements with class blue) |
| .blue.re | All elements with class blue and red (a type of Compound selector) |
| #headline | ID selector (the element with "id" attribute set to headline) |
| :pseudo-class | All elements with pseudo-class |
| ::pseudo-element | Element that matches pseudo-element |
| :lang(en) | Element that matches :lang declaration, for example \<span lang="en"> |
| div > p | child selector |

> **Note:** The value of an ID must be unique in a web page. It is a violation of the HTML standard to use the value of an ID more than
> once in the same document tree.

## Section 4.2: Attribute Selectors

### Overview

Attribute selectors can be used with various types of operators that change the selection criteria accordingly. They select an element using the presence of a given attribute or attribute value.

| Selector | Matched element | Selects elements |
|----------|-----------------|------------------|
| [attr] | \<div attr > | With attribute **attr** |
| [attr='val'] | \<div attr="val" > | Where attribute **attr** has value val |
| [attr~='val'] | \<div attr="val val2 val3" > | Where val appears in the whitespace-separated list of **attr** |
| [attr^='val'] | \<div attr="val1 val2" > | Where **attr**'s value begins with val |
| [attr$='val'] | \<div attr="sth aval" > | Where the **attr**'s value ends with val |
| [attr*='val'] | \<div attr="somevalhere" > | Where **attr** contains val anywhere |
| [attr\|='val'] | \<div attr="val-sth etc" > | Where **attr**'s value is exactly val,or starts with val and immediately followed by (U+002D) |
| [attr='val' i] | \<div attr="val" > | Where **attr** has value val, ignoring val's letter casing |

## Note:

* The attribute value can be surrounded by either single-quotes or double-quotes. No quotes at all may also work, but it's not valid according to the CSS standard, and is discouraged.


### Example

#### [attribute]

Selects elements with the given attribute.

```css
div[data-color] {
  color: red;
}
<div data-color="red">This will be red</div>
<div data-color="green">This will be red</div>
<div data-background="red">This will NOT be red</div>
```

#### [attribute="value"]

Selects elements with the given attribute and value.

```css
div[data-color="red"] {
  color: red;
}
<div data-color="red">This will be red</div>
<div data-color="green">This will NOT be red</div>
<div data-color="blue">This will NOT be red</div>
```

#### [attribute*="value"]

Selects elements with the given attribute and value where the given attribute contains the given value anywhere (as
a substring).

```css
[class*="foo"] {
  color: red;
}
<div class="foo-123">This will be red</div>
<div class="foo123">This will be red</div>
<div class="bar123foo">This will be red</div>
<div class="barfooo123">This will be red</div>
<div class="barfo0">This will NOT be red</div>
```

#### [attribute~="value"]

Selects elements with the given attribute and value where the given value appears in a whitespace-separated list.

```css
[class~="color-red"] {
  color: red;
}
<div class="color-red foo-bar the-div">This will be red</div>
<div class="color-blue foo-bar the-div">This will NOT be red</div>
```

#### [attribute^="value"]

Selects elements with the given attribute and value where the given attribute begins with the value.

```css
[class^="foo-"] {
  color: red;
}
<div class="foo-123">This will be red</div>
<div class="foo-234">This will be red</div>
<div class="bar-123">This will NOT be red</div>
```

#### [attribute$="value"]

Selects elements with the given attribute and value where the given attribute ends with the given value.

```css
[class$="file"] {
  color: red;
}
<div class="foobar-file">This will be red</div>
<div class="foobar-file">This will be red</div>
<div class="foobar-input">This will NOT be red</div>
```

#### [attribute|="value"]

Selects elements with a given attribute and value where the attribute's value is exactly the given value or is exactly
the given value followed by - (U+002D)

```css
[lang|="EN"] {
  color: red;
}
<div lang="EN-us">This will be red</div>
<div lang="EN-gb">This will be red</div>
<div lang="PT-pt">This will NOT be red</div>
```

#### [attribute="value" i]

Selects elements with a given attribute and value where the attribute's value can be represented as Value, VALUE,
vAlUe or any other case-insensitive possibility.

```css
[lang="EN" i] {
  color: red;
}
<div lang="EN">This will be red</div>
<div lang="en">This will be red</div>
<div lang="PT">This will NOT be red</div>
```

#### Specificity of attribute selectors

Same as class selector and pseudoclass.

```css
*[type=checkbox]
```

Note that this means an attribute selector can be used to select an element by its ID at a lower level of specificity than if it was selected with an ID selector: __[id="**my-ID**"]__ targets the same element as __**#my-ID**__ but with lower specificity.

## Section 4.3: Combinators

### Overview

| Selector | Description |
|----------|-------------|
| div span | Descendant selector (all <span>s that are descendants of a <div>) |
| div > span | Child selector (all <span>s that are a direct child of a <div>) |
| a ~ span | General Sibling selector (all <span>s that are siblings after an <a>) |
| a + span | Adjacent Sibling selector (all <span>s that are immediately after an <a>) |

#### Descendant Combinator: selector selector

A descendant combinator, represented by at least one space character (), selects elements that are a descendant of
the defined element. This combinator selects all descendants of the element (from child elements on down).

```css
div p {
  color:red;
}
<div>
  <p>My text is red</p>
  <section>
    <p>My text is red</p>
  </section>
</div>
<p>My text is not red</p>
```

In the above example, the first two <p> elements are selected since they are both descendants of the **<div>**.

#### Child Combinator: selector > selector

The child (>) combinator is used to select elements that are **children**, or **direct descendants**, of the specified element.

```css
div > p {
  color:red;
}
<div>
  <p>My text is red</p>
  <section>
    <p>My text is not red</p>
  </section>
</div>
```

The above CSS selects only the first **<p>** element, as it is the only paragraph directly descended from a **<div>**. 

The second **<p>** element is not selected because it is not a direct child of the **<div>**.

#### Adjacent Sibling Combinator: selector + selector

The adjacent sibling (+) combinator selects a sibling element that immediate follows a specified element.

```css
p+p{
  color:red;
}
<p>My text is not red</p>
<p>My text is red</p>
<p>My text is red</p>
<hr>
<p>My text is not red</p>
```
The above example selects only those **<p>** elements which are directly preceded by another **<p>** element.

#### General Sibling Combinator: selector ~ selector

The general sibling (~) combinator selects all siblings that follow the specified element.

```css
p~p {
  color:red;
}
<p>My text is not red</p>
<p>My text is red</p>
<hr>
<h1>And now a title</h1>
<p>My text is red</p>

```

The above example selects all **<p>** elements that are preceded by another **<p>** element, whether or not they are immediately adjacent.

## Section 4.4: Pseudo-classes

[Pseudo-classes](https://www.w3.org/TR/selectors/#pseudo-classes) are keywords which allow selection based on information that lies outside of the document tree or that cannot be expressed by other selectors or combinators. This information can be associated to a certain state (state and dynamic pseudo-classes), to locations (structural and target pseudo-classes), to negations of the former (negation pseudo-class) or to languages (lang pseudo-class). Examples include whether or not a link has been followed (:visited), the mouse is over an element (:hover), a checkbox is checked (:checked), etc.

### Syntax

```css
selector:pseudo-class {
  property: VALUE;
}
```

### List of pseudo-classes:

| Name | Description |
|------|-------------|
| :active | Applies to any element being activated (i.e. clicked) by the user. |
| :any | Allows you to build sets of related selectors by creating groups that the included items will match. This is an alternative to repeating an entire selector. |
| :target | Selects the current active #news element (clicked on a URL containing that anchor name) |
| :checked | Applies to radio, checkbox, or option elements that are checked or toggled into an "on" state. |
| :default | Represents any user interface element that is the default among a group of similar elements. |
| :disabled | Applies to any UI element which is in a disabled state. |
| :empty | Applies to any element which has no children. |
| :enabled | Applies to any UI element which is in an enabled state. |
| :first | Used in conjunction with the @page rule, this selects the first page in a printed document |
| :first-child | Represents any element that is the first child element of its parent. |
| :first-of-type | Applies when an element is the first of the selected element type inside its parent. This may or may not be the first-child. |
| :focus | Applies to any element which has the user's focus. This can be given by the user's keyboard, mouse events, or other forms of input. |
| :focus-within | Can be used to highlight a whole section when one element inside it is focused. It matches any element that the :focus pseudo-class matches or that has a descendant focused. |
| :full-screen | Applies to any element displayed in full-screen mode. It selects the whole stack of elements and not just the top level element. |
| :hover | Applies to any element being hovered by the user's pointing device, but not activated. |
| :indeterminate | Applies radio or checkbox UI elements which are neither checked nor unchecked, but are in an indeterminate state. This can be due to an element's attribute or DOM manipulation. |
| :in-range | The :in-range CSS pseudo-class matches when an element has its value attribute inside the specified range limitations for this element. It allows the page to give a feedback that the value currently defined using the element is inside the range limits. |
| :invalid | Applies to <input> elements whose values are invalid according to the type specified in the type= attribute. |
| :lang | Applies to any element who's wrapping <body> element has a properly designated lang= attribute. For the pseudo-class to be valid, it must contain a valid two or three letter language code. |
| :last-child | Represents any element that is the last child element of its parent. |
| :last-of-type | Applies when an element is the last of the selected element type inside its parent. This may or may not be the last-child. |
| :left | Used in conjunction with the @page rule, this selects all the left pages in a printed document. |
| :link | Applies to any links which haven't been visited by the user. |
| :not() | Applies to all elements which do not match the value passed to (:not(p) or :not(.class-name) for example. It must have a value to be valid and it can only contain one selector. However, you can chain multiple :not selectors together. |
| :nth-child | Applies when an element is the n-th element of its parent, where n can be an integer, a mathematical expression (e.g n+3) or the keywords odd or even. |
| :nth-of-type | Applies when an element is the n-th element of its parent of the same element type, where n can be an integer, a mathematical expression (e.g n+3) or the keywords odd or even. |
| :only-child | The :only-child CSS pseudo-class represents any element which is the only child of its parent. This is the same as :first-child:last-child or :nth-child(1):nth-last-child(1), but with a lower specificity. |
| :optional | The :optional CSS pseudo-class represents any element that does not have the required attribute set on it. This allows forms to easily indicate optional fields and to style them accordingly. |
| :out-of-range | The :out-of-range CSS pseudo-class matches when an element has its value attribute outside the specified range limitations for this element. It allows the page to give a feedback that the value currently defined using the element is outside the range limits. A value can be outside of a range if it is either smaller or larger than maximum and minimum set values. |
| :placeholder-shown | **Experimental**. Applies to any form element currently displaying placeholder text. |
| :read-only | Applies to any element which is not editable by the user. |
| :read-write | Applies to any element that is editable by a user, such as <input> elements. |
| :right | Used in conjunction with the @page rule, this selects all the right pages in a printed document. |
| :root | matches the root element of a tree representing the document. |
| :scope | CSS pseudo-class matches the elements that are a reference point for selectors to match against. |
| :target | Selects the current active #news element (clicked on a URL containing that anchor name) |
| :visited | Applies to any links which have has been visited by the user. |

## Section 4.5: Child Pseudo Class

> The :nth-child(an+b) CSS pseudo-class matches an element that has an+b-1 siblings before it in the document tree, for a given
> positive **or zero value** for n" - [MDN :nth-child]


| pseudo-selector | 1 2 3 4 5 6 7 8 9 10 |
|-----------------|----------------------|
| :first-child | 1  |
| :nth-child(3) | 3 |
| :nth-child(n+3) | 3 4 5 6 7 8 9 10 |
| :nth-child(3n) | 3 6 9 |
| :nth-child(3n+1) | 1 4 7 10 |
| :nth-child(-n+3) | 1 2 3 |
| :nth-child(odd) | 1 3 5 7 9 |
| :nth-child(even) | 2 4 6 8 10 |
| :last-child | 10 |
| :nth-last-child(3) | 8 |

## Section 4.6: Class Name Selectors

The class name selector select all elements with the targeted class name. For example, the class name .warning would select the following <div> element:

```css
<div class="warning">
  <p>This would be some warning copy.</p>
</div>
```

You can also combine class names to target elements more specifically. Let's build on the example above to showcase a more complicated class selection.

### CSS 

```css
.important {
  color: orange;
}
.warning {
  color: blue;
}
.warning.important {
  color: red;
}
```

### HTML

```html
<div class="warning">
  <p>This would be some warning copy.</p>
</div>
<div class="important warning">
  <p class="important">This is some really important warning copy.</p>
</div>
```

In this example, all elements with the .warning class will have a blue text color, elements with the .important class with have an orange text color, and all elements that have both the .important and .warning class name will have a red text color.


Notice that within the CSS, the .warning.important declaration did not have any spaces between the two class names. This means it will only find elements which contain both class names warning and important in their class attribute. Those class names could be in any order on the element.


If a space was included between the two classes in the CSS declaration, it would only select elements that have parent elements with a .warning class names and child elements with .important class names.

## Section 4.7: Select element using its ID without the high specificity of the ID selector

This trick helps you select an element using the ID as a value for an attribute selector to avoid the high specificity of the ID selector.

### HTML:

```html
<div id="element">...</div>
```

### CSS:

```css
#element { ... } /* High specificity will override many selectors */

[id="element"] { ... } /* Low specificity, can be overridden easily */
```

## Section 4.8: The :last-of-type selector

The __:last-of-type__ selects the element that is the last child, of a particular type, of its parent. In the example below, the css selects the last paragraph and the last heading h1.

```html
p:last-of-type {
  background: #C5CAE9;
}
h1:last-of-type {
  background: #CDDC39;
}

<div class="container">
  <p>First paragraph</p>
  <p>Second paragraph</p>
  <p>Last paragraph</p>
  <h1>Heading 1</h1>
  <h2>First heading 2</h2>
  <h2>Last heading 2</h2>
</div>

```

![Example](http://i.stack.imgur.com/8RYda.png)

## Section 4.9: CSS3 :in-range selector example

```html
<style>
input:in-range {
    border: 1px solid blue;
}
</style>

<input type="number" min="10" max="20" value="15">
<p>The border for this value will be blue</p>
```

The :in-range CSS pseudo-class matches when an element has its value attribute inside the specified range limitations for this element. It allows the page to give a feedback that the value currently defined using the element is inside the range limits.

## Section 4.10: The :not pseudo-class example & B. :focus- within CSS pseudo-class

A. The syntax is presented above.

The following selector matches all <input> elements in an HTML document that are not disabled and don't have the
class .example:

HTML:

```html
<form>
  Phone: <input type="tel" class="example">
  E-mail: <input type="email" disabled="disabled">
  Password: <input type="password">
</form>
```

CSS:

```css
input:not([disabled]):not(.example){
  background-color: #ccc;
}
```

The :not() pseudo-class will also support comma-separated selectors in Selectors Level 4:

CSS:

```css
input:not([disabled], .example){
  background-color: #ccc;
}
```

## The :focus-within CSS pseudo-class

HTML:

```html
<h3>Background is blue if the input is focused .</p>
<div>
  <input type="text">
</div>
```

CSS:

```css
div {
  height: 80px;
}
input {
  margin:30px;
}
div:focus-within {
  background-color: #1565C0;
}

```

![Focus-within example](https://i.stack.imgur.com/S4ke4.png)

![compatibility](https://i.stack.imgur.com/YGn3H.png)

## Section 4.11: Global boolean with checkbox:checked and ~ (general sibling combinator)

With the ~ selector, you can easily implement a global accessible boolean without using JavaScript.

### Add boolean as a checkbox

To the very beginning of your document, add as much booleans as you want with a unique id and the hidden attribute set:

```html
<input type="checkbox" id="sidebarShown" hidden />
<input type="checkbox" id="darkThemeUsed" hidden />
<!-- here begins actual content, for example: -->
<div id="container">
  <div id="sidebar">
        <!-- Menu, Search, ... -->
  </div>
    <!-- Some more content ... -->
</div>
<div id="footer">
  <!-- ... -->
</div>
```

### Change the boolean's value

You can toggle the boolean by adding a label with the for attribute set:

```html
<label for="sidebarShown">Show/Hide the sidebar!</label>
```

### Accessing boolean value with CSS 

The normal selector (like .color-red) specifies the default properties. They can be overridden by following true / false selectors:

```css
/* true: */
<checkbox>:checked ~ [sibling of checkbox & parent of target] <target>
/* false: */
<checkbox>:not(:checked) ~ [sibling of checkbox & parent of target] <target>
```

Note that **<checkbox>**, [sibling ...] and **<target>** should be replaced by the proper selectors. [sibling ...] can be a specific selector, (often if you're lazy) simply * or nothing if the target is already a sibling of the checkbox.

Examples for the above HTML structure would be:

```css
#sidebarShown:checked ~ #container #sidebar {
  margin-left: 300px;
}
#darkThemeUsed:checked ~ #container,
#darkThemeUsed:checked ~ #footer {
  background: #333;
}
```

## Section 4.12: ID selectors

ID selectors select DOM elements with the targeted ID. To select an element by a specific ID in CSS, the # prefix is used.

For example, the following HTML div element...

```css
<div id="exampleID">
  <p>Example</p>
</div>
```

...can be selected by #exampleID in CSS as shown below:

```css
#exampleID {
  width: 20px;
}
```

> **Note**: The HTML specs do not allow multiple elements with the same ID


## Section 4.13: How to style a Range input

### HTML

```html
<input type="range"></input>
```
### CSS

| Effect | Pseudo Selector |
|--------|-----------------|
| Thumb | input[type=range]::-webkit-slider-thumb, input[type=range]::-moz-range-thumb, input[type=range]::-ms-thumb |
| Track | input[type=range]::-webkit-slider-runnable-track, input[type=range]::-moz-range-track, input[type=range]::-ms-track |
| OnFocus | input[type=range]:focus |
| Lower part of the track | input[type=range]::-moz-range-progress, input[type=range]::-ms-fill-lower (not possible in WebKit browsers currently - JS needed) |

## Section 4.14: The :only-child pseudo-class selector example

The :only-child CSS pseudo-class represents any element which is the only child of its parent.

### HTML:

```html
<div>
  <p>This paragraph is the only child of the div, it will have the color blue</p>
</div>
<div>
  <p>This paragraph is one of the two children of the div</p>
  <p>This paragraph is one of the two children of its parent</p>
</div>
```

### CSS:

```css
p:only-child {
  color: blue;
}
```

The above example selects the **<p>** element that is the unique child from its parent, in this case a **<div>**.












 

