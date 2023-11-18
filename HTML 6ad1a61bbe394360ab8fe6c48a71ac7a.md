# HTML

**Tags** 

<button> : a clickable button

```html
<button type= "botton">Save</button> 
```

<iframe> : it is a tag that specifies an inline frame which is used to embed another document within the current HTML document.

```html
<iframe src= "https://maps.app.goo.gl/ZvtTmyjoxivH8ZJ4A" title = "British Council "> Location</iframe>
```

<section>: Represents a standalone section within a document.

```html
<section><h2>About Us</h2><p>Some information about our company.</p></section>
```

<blockquote>: Represents a section that is quoted from another source.

```html
<blockquote>"Quote goes here."</blockquote>
```

<pre>: Represents preformatted text, preserving spaces and line breaks.

```html
<pre>This is preformatted text.</pre>
```

<aside>: Represents content that is tangentially related to the main content.

```html
<aside>Related links or additional information.</aside>
```

Embed: 

<div>: element is by default a block element, meaning that it takes all available width, and comes with line breaks before and after.

```html
Lorem Ipsum <div>I am a div</div> dolor sit amet.
```

<keygen>: Generates a key pair for use in forms.

```html
<keygen name="myKey">
```

<output>: Displays the result of a calculation or user action.

```html
<output for="myRange">50</output>
```

<track>: Specifies text tracks for media elements, such as subtitles or captions.

```html
<track src="subtitles.vtt" kind="subtitles" srclang="en" label="English">
```

The HTML `<form>` element is used to create an HTML form for user input. The `<form>` element is a container for different types of input elements, such as: text fields, checkboxes, radio buttons, submit buttons, etc.

```html
<form>.*form elements*.</form>
```

An `<input>` element can be displayed in many ways, depending on the `type` attribute.

The `<input type="text">` defines a single-line input field for text input.

```html
<form>
  <label for="fname">First name:</label><br>
  <input type="text" id="fname" name="fname"><br>
  <label for="lname">Last name:</label><br>
  <input type="text" id="lname" name="lname">
</form>
```

The `<label>` tag defines a label for many form elements.

The `<label>` element is useful for screen-reader users, because the screen-reader will read out loud the label when the user focuses on the input element.

The `<label>` element also helps users who have difficulty clicking on very small regions (such as radio buttons or checkboxes) - because when the user clicks the text within the `<label>` element, it toggles the radio button/checkbox.

The `for` attribute of the `<label>` tag should be equal to the `id` attribute of the `<input>` element to bind them together.

The `<input type="radio">` defines a radio button.

Radio buttons let a user select ONE of a limited number of choices.

```html
<p>Choose your favorite Web language:</p>

<form>
  <input type="radio" id="html" name="fav_language" value="HTML">
  <label for="html">HTML</label><br>
  <input type="radio" id="css" name="fav_language" value="CSS">
  <label for="css">CSS</label><br>
  <input type="radio" id="javascript" name="fav_language" value="JavaScript">
  <label for="javascript">JavaScript</label>
</form>
```

The `<input type="checkbox">` defines a **checkbox**.

Checkboxes let a user select ZERO or MORE options of a limited number of choices.

```html
<form>
  <input type="checkbox" id="vehicle1" name="vehicle1" value="Bike">
  <label for="vehicle1"> I have a bike</label><br>
  <input type="checkbox" id="vehicle2" name="vehicle2" value="Car">
  <label for="vehicle2"> I have a car</label><br>
  <input type="checkbox" id="vehicle3" name="vehicle3" value="Boat">
  <label for="vehicle3"> I have a boat</label>
</form>
```

The `<input type="submit">` defines a button for submitting the form data to a form-handler.

The form-handler is typically a file on the server with a script for processing input data.

The form-handler is specified in the form's `action` attribute.

```html
<form action="/action_page.php">
  <label for="fname">First name:</label><br>
  <input type="text" id="fname" name="fname" value="John"><br>
  <label for="lname">Last name:</label><br>
  <input type="text" id="lname" name="lname" value="Doe"><br><br>
  <input type="submit" value="Submit">
</form>
```