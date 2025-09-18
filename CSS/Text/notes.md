# ✒️ All About CSS Fonts

Fonts are a crucial aspect of web design, influencing readability, aesthetics, and user experience. CSS provides a powerful set of properties to control every aspect of text styling on your web pages.

## Understanding CSS Font Properties

CSS offers various properties to style your text, from the font type to its size, weight, and spacing.

### 1. `font-family`

The `font-family` property specifies the font for an element. It can hold several font names as a "fallback" system. The browser will try to find the first font, if not available, it will try the next, and so on.

* **Syntax:** `font-family: "Font Name", Generic-Family, "Another Font";`
* **Generic Families:** Always include a generic family as a last resort:
    * `serif` (e.g., Times New Roman, Georgia)
    * `sans-serif` (e.g., Arial, Helvetica, Verdana)
    * `monospace` (e.g., Courier New, Consolas)
    * `cursive` (e.g., Comic Sans MS, Brush Script MT)
    * `fantasy` (e.g., Impact, Copperplate)

**Example:**

```css
p {
  font-family: "Helvetica Neue", Arial, sans-serif;
}

h1 {
  font-family: Georgia, serif;
}
```

### 2. `font-size`

The `font-size` property sets the size of the text.

* **Syntax:** `font-size: value;`
* **Units:**
    * **`px` (pixels):** Absolute unit. Consistent across devices but doesn't scale with user preferences.
    * **`em` (relative to parent's font-size):** `2em` means 2 times the font size of the parent element. Scales well but can be complex in nested elements.
    * **`rem` (relative to root font-size):** `2rem` means 2 times the font size of the `<html>` (root) element. More predictable and easier to manage than `em` for overall scaling.
    * **`%` (percentage):** Relative to the parent's font size. `100%` is default.
    * **`vw` (viewport width):** `1vw` is 1% of the viewport width. Good for fluid typography.
    * **Keywords:** `small`, `medium`, `large`, `x-small`, `xx-small`, `x-large`, `xx-large`, `smaller`, `larger`.

**Example:**

```css
body {
  font-size: 16px; /* Base size */
}

h2 {
  font-size: 2.5rem; /* 2.5 times the root font size */
}

.intro-text {
  font-size: 1.2em; /* 1.2 times its parent's font size */
}
```

### 3. `font-weight`

The `font-weight` property sets how thick or thin characters in text should be displayed.

* **Syntax:** `font-weight: value;`
* **Values:**
    * **Keywords:** `normal` (400), `bold` (700), `lighter`, `bolder`.
    * **Numbers:** `100` to `900` (in multiples of 100). Not all fonts support all weights. `400` is `normal`, `700` is `bold`.

**Example:**

```css
h3 {
  font-weight: bold;
}

.thin-text {
  font-weight: 300; /* Lighter than normal */
}
```

### 4. `font-style`

The `font-style` property specifies the font style for text.

* **Syntax:** `font-style: value;`
* **Values:**
    * `normal`: Default text.
    * `italic`: Text is italicized.
    * `oblique`: Text is "slanted" but not necessarily true italic (some fonts don't have true italic versions).

**Example:**

```css
em {
  font-style: italic;
}

.special-note {
  font-style: oblique;
}
```

### 5. `font-variant`

The `font-variant` property specifies whether a text should be displayed in a small-caps font.

* **Syntax:** `font-variant: value;`
* **Values:**
    * `normal`: Default.
    * `small-caps`: Converts all lowercase letters to uppercase letters but in a smaller size than the original uppercase letters.

**Example:**

```css
h4 {
  font-variant: small-caps;
}
```

### 6. `line-height`

The `line-height` property specifies the height of a line of text, influencing the vertical spacing between lines.

* **Syntax:** `line-height: value;`
* **Values:**
    * **`normal`:** Default browser value (typically around 1.2).
    * **Number (unitless):** Recommended. Multiplies the `font-size` to determine the line height (e.g., `1.5` means 1.5 times the font size). This value scales proportionally with font size changes.
    * **Length (px, em, rem):** Absolute values.
    * **Percentage:** Relative to the element's own font size.

**Example:**

```css
p {
  line-height: 1.6; /* Recommended for readability */
}

h5 {
  line-height: 1.2em;
}
```

### 7. `text-align`

The `text-align` property specifies the horizontal alignment of text within an element.

* **Syntax:** `text-align: value;`
* **Values:** `left`, `right`, `center`, `justify`.

**Example:**

```css
.header-text {
  text-align: center;
}

.article-content {
  text-align: justify;
}
```

### 8. `text-decoration`

The `text-decoration` property specifies the lines that are added to text (e.g., underline, overline, line-through).

* **Syntax:** `text-decoration: none | [ line-style line-color line-type ];`
* **Values:**
    * `none`: Removes any decoration (common for links).
    * `underline`: Underlines the text.
    * `overline`: Puts a line above the text.
    * `line-through`: Puts a line through the text.
    * You can also specify `line-style` (e.g., `solid`, `double`, `dotted`, `dashed`, `wavy`) and `line-color`.

**Example:**

```css
a {
  text-decoration: none; /* Remove default underline from links */
}

.strike-through {
  text-decoration: line-through red wavy;
}
```

### 9. `text-transform`

The `text-transform` property controls the capitalization of text.

* **Syntax:** `text-transform: value;`
* **Values:**
    * `none`: No capitalization.
    * `uppercase`: Converts all characters to uppercase.
    * `lowercase`: Converts all characters to lowercase.
    * `capitalize`: Capitalizes the first letter of each word.

**Example:**

```css
h6 {
  text-transform: uppercase;
}

.recipe-title {
  text-transform: capitalize;
}
```

### 10. `letter-spacing` and `word-spacing`

* **`letter-spacing`**: Specifies the space between characters.
* **`word-spacing`**: Specifies the space between words.

**Syntax:**
`letter-spacing: length;`
`word-spacing: length;`

**Example:**

```css
.spaced-text {
  letter-spacing: 2px;
  word-spacing: 5px;
}
```

### 11. `text-shadow`

The `text-shadow` property adds a shadow to text.

* **Syntax:** `text-shadow: h-shadow v-shadow blur-radius color;`
    * `h-shadow`: Required. Horizontal position of the shadow.
    * `v-shadow`: Required. Vertical position of the shadow.
    * `blur-radius`: Optional. The blur distance.
    * `color`: Optional. The color of the shadow.

**Example:**

```css
.fancy-text {
  text-shadow: 2px 2px 4px #aaa;
}
```

### 12. `@font-face` Rule (Importing Custom Fonts)

The `@font-face` CSS rule allows you to define custom fonts that should be loaded. This is essential for using fonts not commonly installed on users' systems.

* **`font-family`**: The name you want to give the font (used in `font-family` property later).
* **`src`**: The URL to the font file(s). Provide multiple formats for broader browser support (`.woff2`, `.woff`, `.ttf`, `.otf`, `.svg`, `.eot`).
* **`font-weight` / `font-style`**: Optional. If you're importing different weights/styles of the same font, you can specify them here.

**Example:**

```css
@font-face {
  font-family: "MyCustomFont";
  src: url("fonts/mycustomfont-regular.woff2") format("woff2"),
       url("fonts/mycustomfont-regular.woff") format("woff");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "MyCustomFont"; /* Same family name */
  src: url("fonts/mycustomfont-bold.woff2") format("woff2"),
       url("fonts/mycustomfont-bold.woff") format("woff");
  font-weight: bold; /* Different weight */
  font-style: normal;
}

body {
  font-family: "MyCustomFont", Arial, sans-serif;
}
```

### 13. `font` Shorthand Property

The `font` shorthand property allows you to set several font properties in one declaration, making your CSS more concise.

* **Order (required):** `font-style font-variant font-weight font-size/line-height font-family`
* **Note:** `font-size` and `font-family` are required. If `font-style`, `font-variant`, and `font-weight` are omitted, their initial values will be used.

**Example:**

```css
p {
  font: italic small-caps bold 1.2em/1.5 "Times New Roman", serif;
  /* This sets:
     font-style: italic;
     font-variant: small-caps;
     font-weight: bold;
     font-size: 1.2em;
     line-height: 1.5;
     font-family: "Times New Roman", serif;
  */
}

.simple-text {
  font: 16px Arial, sans-serif; /* Sets font-size and font-family */
}
