# JSON Formatter

A small, browser-based JSON formatter built with **HTML, CSS, and JavaScript**.

I made this project to keep working with JSON simple: paste your JSON, click **Format JSON**, and get a clean, readable version. It also shows a clear error message when the JSON is not valid.

## Preview

The page has a simple layout with:

- A JSON editor
- A **Format JSON** button
- A **Clear** button
- A message area for success and error messages

> Add a screenshot of the project here.

```md
![JSON Formatter Screenshot](./screenshot.png)
```

## Features

- Format and indent JSON automatically
- Validate JSON before formatting
- Show the actual parsing error when the JSON is invalid
- Clear the editor with one click
- Simple and responsive interface
- No backend or database required
- Works directly in the browser

## How It Works

The main idea is pretty straightforward.

When the **Format JSON** button is clicked, the application tries to parse the text using JavaScript's `JSON.parse()`:

```javascript
const json = JSON.parse(editor.value);
```

If the JSON is valid, it is converted back to a formatted string using `JSON.stringify()`:

```javascript
editor.value = JSON.stringify(json, null, 4);
```

The `4` means that nested values are indented by four spaces.

If parsing fails, the error is caught and displayed below the buttons:

```javascript
catch (error) {
    message.textContent = "Invalid JSON: " + error.message;
}
```

This makes it easy to find problems instead of getting a generic error.

## Example

### Before

```json
{"name":"John","age":25,"skills":["PHP","Laravel","JavaScript"],"active":true}
```

### After

```json
{
    "name": "John",
    "age": 25,
    "skills": [
        "PHP",
        "Laravel",
        "JavaScript"
    ],
    "active": true
}
```

## Running the Project

No installation is required.

1. Clone or download the project.
2. Open `index.html` in your browser.
3. Paste your JSON into the editor.
4. Click **Format JSON**.


## Custom JSON Editor

The project also includes a custom `<json-editor>` Web Component.

It uses **Shadow DOM** and a `contentEditable` element to create a more advanced JSON editing experience. The component can parse JSON and format different values separately, including:

- Objects
- Arrays
- Strings
- Numbers
- Booleans
- `null`

Different JSON parts can also be styled with CSS using the `part` attribute, for example:

```html
<span part="number">25</span>
<span part="string">"Laravel"</span>
<span part="true">true</span>
```

This makes it possible to build a syntax-highlighted JSON editor without depending on a large external editor library.

## Technologies

- HTML5
- CSS3
- JavaScript
- Web Components
- Shadow DOM
- `contentEditable`
- Native JavaScript JSON API

## What I Learned

While building this project, I worked with a few useful browser and JavaScript concepts:

- Parsing JSON with `JSON.parse()`
- Formatting JSON with `JSON.stringify()`
- Handling errors with `try...catch`
- Updating the DOM with JavaScript
- Creating custom Web Components
- Working with Shadow DOM
- Using `contentEditable` for browser-based editors

## Possible Improvements

There are a few things I would like to add in a future version:

- Copy formatted JSON to the clipboard
- Download JSON as a `.json` file
- Minify JSON
- Better syntax highlighting
- Dark mode
- Drag and drop a JSON file
- Live formatting while typing
- Line numbers
- Better handling of very large JSON files