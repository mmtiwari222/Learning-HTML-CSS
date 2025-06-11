# 🎨 Introduction to CSS Selector

Welcome to this repository, your starting point for understanding Cascading Style Sheets (CSS)! If you're looking to make your web pages visually appealing and engaging, you've come to the right place.


* **Selector:** Points to the HTML element you want to style.
    * Example: `h1`, `p`, `.container`, `#main-navigation`
* **Declaration Block:** Contains one or more declarations separated by semicolons.
* **Declaration:** Includes a CSS property name and a value, separated by a colon.
    * **Property:** The style attribute you want to change (e.g., `color`, `font-size`, `margin`).
    * **Value:** The value for the given property (e.g., `blue`, `16px`, `20px auto`).

**Example:**

```css
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
}

h2 {
  color: #336699;
  text-align: center;
}
```

## CSS Order and Priority (The Cascade)

The "Cascading" in CSS refers to how the browser determines which styles to apply when multiple rules target the same element. It follows a specific order of priority:

1.  **Importance:** The `!important` rule overrides any other declaration, regardless of specificity. Use it sparingly, as it can make debugging difficult.
    ```css
    p {
      color: blue !important; /* This will always be blue */
    }
    ```
2.  **Specificity:** This is a crucial concept. The browser calculates a "specificity score" for each selector based on the types of selectors used:
    * **Inline styles:** Highest specificity (1,0,0,0)
    * **IDs:** (0,1,0,0)
    * **Classes, pseudo-classes, attribute selectors:** (0,0,1,0)
    * **Elements (type), pseudo-elements:** (0,0,0,1)
    * **Universal selector (`*`), combinators (`+`, `>`), negation pseudo-class (`:not()`):** (0,0,0,0) - they don't add to specificity
    * **Example:**
        ```css
        /* Specificity: (0,0,1,0) */
        .my-text {
          color: red;
        }

        /* Specificity: (0,0,0,1) */
        p {
          color: blue;
        }

        /* The text with class 'my-text' will be red. */
        ```
3.  **Order of Appearance:** If rules have the same specificity, the last rule declared in the stylesheet (or the last linked stylesheet) takes precedence.
    ```css
    p {
      color: green; /* This will be overridden */
    }
    p {
      color: purple; /* This will apply */
    }
    ```
4.  **Source Order (Origin):** Styles come from different sources:
    * **Author Styles:** Styles defined by the web developer (your CSS).
    * **User Styles:** Styles defined by the user (e.g., through browser extensions).
    * **Browser Defaults:** Default styles applied by the web browser.
    * Author styles generally override user styles, which in turn override browser defaults.

## All About CSS Selectors

CSS selectors are patterns used to select the HTML elements you want to style. Mastering them is key to efficient and precise styling.

### Basic Selectors

1.  **Universal Selector (`*`)**
    * Selects all HTML elements on the page.
    ```css
    * {
      box-sizing: border-box; /* Common use case */
    }
    ```

2.  **Type (Element) Selectors**
    * Selects all instances of a specific HTML element type.
    ```css
    p {
      line-height: 1.5;
    }

    a {
      text-decoration: none;
    }
    ```

3.  **Class Selectors (`.`)**
    * Selects elements with a specific `class` attribute. Elements can have multiple classes.
    ```html
    <div class="card">...</div>
    <p class="text-primary">...</p>
    ```css
    .card {
      border: 1px solid #ccc;
      padding: 15px;
    }

    .text-primary {
      color: blue;
    }
    ```

4.  **ID Selectors (`#`)**
    * Selects a single, unique element with a specific `id` attribute. An `id` should be unique within a page.
    ```html
    <nav id="main-navigation">...</nav>
    ```css
    #main-navigation {
      background-color: #333;
      color: white;
    }
    ```

### Attribute Selectors

Select elements based on the presence or value of an HTML attribute.

* **`[attribute]`**: Selects elements with the specified attribute.
    ```css
    a[target] { /* Selects all <a> elements with a 'target' attribute */
      text-decoration: underline;
    }
    ```
* **`[attribute="value"]`**: Selects elements where the attribute has an exact value.
    ```css
    input[type="text"] { /* Selects <input> elements with type="text" */
      border: 1px solid gray;
    }
    ```
* **`[attribute~="value"]`**: Selects elements where the attribute's value contains a specified word (space-separated).
    ```css
    p[class~="highlight"] { /* Selects <p> with 'highlight' as one of its classes */
      background-color: yellow;
    }
    ```
* **`[attribute|="value"]`**: Selects elements where the attribute's value starts with the specified value, followed by a hyphen (`-`). Often used for language codes.
    ```css
    div[lang|="en"] { /* Selects <div> elements with lang="en" or lang="en-us" etc. */
      font-family: sans-serif;
    }
    ```
* **`[attribute^="value"]`**: Selects elements where the attribute's value *starts with* the specified value.
    ```css
    a[href^="https://"] { /* Selects <a> elements whose href starts with "https://" */
      color: green;
    }
    ```
* **`[attribute$="value"]`**: Selects elements where the attribute's value *ends with* the specified value.
    ```css
    img[src$=".png"] { /* Selects <img> elements whose src ends with ".png" */
      border: 2px solid blue;
    }
    ```
* **`[attribute*="value"]`**: Selects elements where the attribute's value *contains* the specified value anywhere.
    ```css
    [title*="important"] { /* Selects elements whose title contains "important" */
      font-weight: bold;
    }
    ```

### Combinators

Combinators explain the relationship between selectors.

1.  **Descendant Selector (Space)**
    * Selects all elements that are descendants of a specified element (can be nested at any level).
    ```css
    div p { /* Selects all <p> elements inside any <div> */
      margin-bottom: 10px;
    }
    ```

2.  **Child Selector (`>`)**
    * Selects all elements that are *direct children* of a specified element.
    ```css
    ul > li { /* Selects all <li> elements that are direct children of a <ul> */
      list-style-type: square;
    }
    ```

3.  **Adjacent Sibling Selector (`+`)**
    * Selects an element that is the *immediately following sibling* of a specified element.
    ```css
    h1 + p { /* Selects the first <p> element immediately after an <h1> */
      font-style: italic;
    }
    ```

4.  **General Sibling Selector (`~`)**
    * Selects all elements that are siblings of a specified element, even if not immediately adjacent, as long as they follow it.
    ```css
    h2 ~ p { /* Selects all <p> elements that are siblings of an <h2> and come after it */
      text-indent: 20px;
    }
    ```

### Pseudo-classes

Pseudo-classes are used to define a special state of an element.

* **`:hover`**: When the user mouses over an element.
    ```css
    a:hover {
      color: red;
    }
    ```
* **`:active`**: When an element is being activated (e.g., clicked).
* **`:focus`**: When an element has focus (e.g., an input field).
* **`:visited`**: For links that have been visited.
* **`:link`**: For unvisited links.
* **`:first-child`**: Selects the first child element of its parent.
    ```css
    li:first-child {
      font-weight: bold;
    }
    ```
* **`:last-child`**: Selects the last child element.
* **`:nth-child(n)`**: Selects every `n`th child element. `n` can be a number, `odd`, `even`, or a formula like `2n+1`.
    ```css
    li:nth-child(even) {
      background-color: #f2f2f2;
    }
    ```
* **`:not(selector)`**: Selects elements that do NOT match the specified selector.
    ```css
    button:not(.disabled) {
      cursor: pointer;
    }
    ```
* **`:empty`**: Selects elements that have no children (including text nodes).
* **`:checked`**: Selects checked radio buttons or checkboxes.
* **`:enabled`, `:disabled`**: Selects enabled or disabled input elements.

### Pseudo-elements

Pseudo-elements are used to style a specific part of an element. They are denoted by `::` (though single colon `:` is also supported for older syntax, `::` is preferred).

* **`::before`**: Inserts content before the content of an element. Requires the `content` property.
    ```css
    h2::before {
      content: "⭐ ";
      color: gold;
    }
    ```
* **`::after`**: Inserts content after the content of an element. Requires the `content` property.
    ```css
    a::after {
      content: " ↗";
    }
    ```
* **`::first-line`**: Selects the first line of a text block.
    ```css
    p::first-line {
      font-variant: small-caps;
    }
    ```
* **`::first-letter`**: Selects the first letter of a text block.
    ```css
    p::first-letter {
      font-size: 2em;
      float: left;
      margin-right: 5px;
    }
    ```
* **`::selection`**: Styles the portion of an element that is selected by the user.
    ```css
    ::selection {
      background-color: yellow;
      color: black;
    }
    ```

### Grouping Selectors

* **Grouping (Comma `,`)**: Groups multiple selectors to apply the same styles to all of them.
    ```css
    h1, h2, h3 {
      font-family: sans-serif;
      color: #333;
    }
    ```

---

Feel free to explore the examples and code within this repository to deepen your understanding of CSS. Happy styling!

---
