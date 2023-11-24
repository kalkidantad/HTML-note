# CSS

There are three ways to insert CSS. 

1. **External :** 

They are defined within the <link> element, inside the <head> section of an HTML page. An external style sheet can be written in any text editor, and must be saved with a `.css` extension.

```html
<!DOCTYPE html><html>
<head>
<link rel="stylesheet" href="mystyle.css">
</head>
<body>
<h1>This is a heading</h1>
<p>This is a paragraph.</p>
</body>
</html>
```

```css
body {
  background-color: lightblue;
}

h1 {
  color: navy;
  margin-left: 20px;
}
```

1. **Internal CSS :** 

An internal style sheet may be used if one single HTML page has a unique style.

The internal style is defined inside the <style> element, inside the head section like shown below.

```html
<!DOCTYPE html>
<html>
<head>
<style>
body {
  background-color: linen;
}

h1 {
  color: maroon;
  margin-left: 40px;
}
</style>
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
</html>
```

1. Inline CSS : To use inline styles, add the style attribute to the relevant element. The style attribute can contain any CSS property.

```html
<!DOCTYPE html>
<html>
<body>

<h1 style="color:blue;text-align:center;">This is a heading</h1>
<p style="color:red;">This is a paragraph.</p>

</body>
</html>
```

**CSS Comments :**

Comments are used to explain the code, and may help when you edit the source code at a later date.

Comments are ignored by browsers. It can either be used for multiple lines of comment and also single line as displayed on the example.

A CSS comment is placed inside the `<style>` element, and starts with `/*` and ends with `*/`:

```css
/* This is a single-line comment */
p {
  color: red;
}
```

**CSS Margins** 

Margins are used to create space around elements, outside of any defined borders.

```html
<style>
div {
  margin: 100px;
  border: 1px solid #4CAF50;
}
</style>
```

CSS has properties for specifying the margin for each side of an element:

- `margin-top`
- `margin-right`
- `margin-bottom`
- `margin-left`

```css
p {
  margin-top: 100px;
  margin-bottom: 100px;
  margin-right: 150px;
  margin-left: 80px;
}
```

**CSS Padding**

Padding is used to create space around an element's content, inside of any defined borders.

```html
<style>
div {
  padding: 70px;
  border: 1px solid #4CAF50;
}
</style>
```

**CSS Box Model :**

The CSS box model is essentially a box that wraps around every HTML element. It consists of: content, padding, borders and margins. The image below illustrates the box model:

```css
div {
  width: 300px;
  border: 15px solid green;
  padding: 50px;
  margin: 20px;
}
```

**CSS Icons**

Icons can easily be added to your HTML page, by using an icon library.

```html
<script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
</head>
<body>

<i class="fas fa-cloud"></i>
<i class="fas fa-heart"></i>
<i class="fas fa-car"></i>
<i class="fas fa-file"></i>
<i class="fas fa-bars"></i>

</body>
```

**CSS Tables:** **Table with merged cells**: This table has merged cells in the first row and first column.

```css
<style>
table, th, td {
  border: 1px solid;
}

table {
  width: 100%;
}
</style>
<table>
  <tr>
    <th rowspan="2">Header 1</th>
    <th>Header 2</th>
    <th>Header 3</th>
  </tr>
  <tr>
    <td>Data 1</td>
    <td>Data 2</td>
  </tr>
  <tr>
    <td>Data 3</td>
    <td>Data 4</td>
    <td>Data 5</td>
  </tr>
</table>

```

Table With Nested Tables:

```css
<style>
table, th, td {
  border: 1px solid;
}

table {
  width: 100%;
}
</style>
<table>
  <tr>
    <th>Column 1</th>
    <th>Column 2</th>
  </tr>
  <tr>
    <td>Data 1</td>
    <td>
      <table>
        <tr>
          <th>Nested Column 1</th>
          <th>Nested Column 2</th>
        </tr>
        <tr>
          <td>Nested Data 1</td>
          <td>Nested Data 2</td>
        </tr>
      </table>
    </td>
  </tr>
</table>
```

**CSS FLOAT**

The CSS `float` property specifies how an element should float.

The CSS `clear` property specifies what elements can float beside the cleared element and on which side.

The `float` property is used for positioning and formatting content e.g. let an image float left to the text in a container.

The `float` property can have one of the following values:

- `left` - The element floats to the left of its container
- `right` - The element floats to the right of its container
- `none` - The element does not float (will be displayed just where it occurs in the text). This is default
- `inherit` - The element inherits the float value of its parent

In its simplest use, the `float` property can be used to wrap text around images.

```css
img {
  float: right;
}
/*other options of value include left, none*/
```

**CSS COMBINATOR**

A combinator is something that explains the relationship between the selectors.

A CSS selector can contain more than one simple selector. Between the simple selectors, we can include a combinator.

There are four different combinators in CSS:

- descendant selector (space)
- child selector (>)
- adjacent sibling selector (+)
- general sibling selector (~)

The descendant selector matches all elements that are descendants of a specified element.

The following example selects all <p> elements inside <div> elements:

```css
div p {
  background-color: yellow;
}
```

The child selector selects all elements that are the children of a specified element.

The following example selects all <p> elements that are children of a <div> element:

```css
div > p {
  background-color: yellow;
}
```

The adjacent sibling selector is used to select an element that is directly after another specific element.

Sibling elements must have the same parent element, and "adjacent" means "immediately following".

The following example selects the first <p> element that are placed immediately after <div> elements:

```css
div + p {
  background-color: yellow;
}
```

The general sibling selector selects all elements that are next siblings of a specified element.

The following example selects all <p> elements that are next siblings of <div> elements:

```css
div ~ p {
  background-color: yellow;
}
```

**CSS DROPDOWN**

Create a hoverable dropdown with CSS.

```html
<style>
.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  padding: 12px 16px;
  z-index: 1;
}

.dropdown:hover .dropdown-content {
  display: block;
}
</style>

<div class="dropdown">
  <span>Mouse over me</span>
  <div class="dropdown-content">
    <p>Hello World!</p>
  </div>
</div>
```

**CSS FORMS**

Use the `padding` property to add space inside the text field.

**Tip:** When you have many inputs after each other, you might also want to add some `margin`, to add more space outside of them:

```css
input[type=text] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
}
```

If you only want a bottom border, use the `border-bottom` property:

```css
input[type=text] {
  border: none;
  border-bottom: 2px solid red;
}
```

By default, some browsers will add a blue outline around the input when it gets focus (clicked on). You can remove this behavior by adding `outline: none;` to the input.

Use the `:focus` selector to do something with the input field when it gets focus:

```css
input[type=text]:focus {
  background-color: lightblue;
}
```

If you want an icon inside the input, use the `background-image` property and position it with the `background-position` property. Also notice that we add a large left padding to reserve the space of the icon:

```css
input[type=text] {
  background-color: white;
  background-image: url('searchicon.png');
  background-position: 10px 10px;
  background-repeat: no-repeat;
  padding-left: 40px;
}
```

In this example we use the CSS `transition` property to animate the width of the search input when it gets focus.

```css
input[type=text] {
  transition: width 0.4s ease-in-out;
}

input[type=text]:focus {
  width: 100%;
}
```

Use the `resize` property to prevent textareas from being resized (disable the "grabber" in the bottom right corner):

```css
textarea {
  width: 100%;
  height: 150px;
  padding: 12px 20px;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 4px;
  background-color: #f8f8f8;
  resize: none;
}
```

**STYLING SELECT MENUS**

```html
<html>
<head>
<style> 
select {
  width: 100%;
  padding: 16px 20px;
  border: none;
  border-radius: 4px;
  background-color: #f1f1f1;
}
</style>
</head>
<body>

<h2>Styling a select menu</h2>

<form>
  <select id="country" name="country">
  <option value="au">Australia</option>
  <option value="ca">Canada</option>
  <option value="usa">USA</option>
  </select>
</form>
```

**STYLING INPUT BUTTONS**

```css
input[type=button], input[type=submit], input[type=reset] {
  background-color: #04AA6D;
  border: none;
  color: white;
  padding: 16px 32px;
  text-decoration: none;
  margin: 4px 2px;
  cursor: pointer;
}
```