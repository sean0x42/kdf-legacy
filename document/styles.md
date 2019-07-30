# Styles

This specification defines a system of classifying and styling textual content
in Kauri Document Format (KDF), using CSS expressions and classes.


## Table of Contents

 1. [Glossary](#glossary)
 2. [Heirarchy](#heirarchy)
 3. [File Format](#file-format)
 4. [Page Styles](#page-styles)
    1. [`size`](#size)
       - [Page size constants](#page-size-constants)
    2. [`orientation`](#orientation)
    3. [Padding and Margins](#padding-and-margins)
 5. [Style Classes](#style-classes)
    1. [`display`](#display)
    2. [`styles`](#styles)
    3. [`inherit`](#inherit)


## Glossary

 - **Human readable**: A string that is designed to be consumed by *any*
   possible user. Including users with no technical expertise or experience.

 - **JSON**: JavaScript Object Notation.

   > A lightweight data-interchange format. It is easy for humans to read and
   > write. It is easy for machines to parse and generate.  
   > — [json.org](https://json.org/)

 - **CSS**: Cascading Style Sheets

   > ...a language used to describe the presentation of a document written in
   > HTML or XML. ...CSS describes how elements should be rendered on screen...  
   > — [MDN (developer.mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/CSS)

 - **CSS expression**: A CSS property-value pair. e.g. `color: red;`.

 - **Case-insensitive**: An operation which ignores the case of a string. i.e.
   `Hello World` is considered to be equal to `HELLO WORLD`.

 - **Case-sensitive**: The opposite of *case-insensitive*.


## Heirarchy

Styles are composed in JavaScript Object Notation (JSON), and are contained
within a single, root JSON object with the following keys:

 - `page` — A JSON object, which defines the appearance of each page.
 - `classes` — A JSON object, which enumerates all available style classes.

For example:

```json
{
  "page": {
    "size": "A4",
    "orientation": "portrait",
    "margin": "2cm 3cm"
  },
  "classes": {
    "fig": { }
  }
}
```


## File Format

When storing styles in the Kauri Document Format, serialize the root JSON
object to a file called `styles.json`, in the root directory of the document
archive.



## Page Styles

The `page` styles JSON object, contains zero or more key-value pairs, which
describe the appearance of each page. You may use any valid CSS expression, or
one of the custom style expressions described in the sections below.

### `size`

| Property       | Value   |
|:---------------|:--------|
| Type           | String  |
| Required       | ❌      |
| Default        | `"A4"`  |
| Case-sensitive | ❌      |

A string, containing a [*page size constant*](#page-size-constants). A default
value of `A4` is assumed when no value is given.

```json
{
  "page": {
    "size": "Letter"
  }
}
```

The CSS properties `height` and `width` will always take precedence over the
`size`, effectively overriding it within one axis. Consider the following JSON
snippet:

```json
{
  "page": {
    "size": "A4",
    "height": "100mm"
  }
}
```

This page could be described with the following CSS:

```css
.page {
  height: 100mm; /* Overrides 297mm */
  width: 210mm;
}
```


#### Page size constants

The following page size constants are currently available for use (more may be
added in future):

 - **A and B Series**: As defined by ISO 216. e.g. `A4`, `B9` etc.

 - **C Series**: As defined by ISO 269. e.g. `C1`, `C2`, or `C5`.

 - **Common US Loose Sizes**: The following four sizes are available: `Letter`,
   `Legal`, `Tabloid`, and `Ledger`.

 - **US ANSI Series**: As defined by ANSI/ASME Y14.1 and Y14.1M. e.g. `ANSI A`,
   ..., `ANSI K`.

 - **US ARCH Series**: As defined by ANSI/ASME Y14.1 and Y14.1M. e.g. `ARCH A`,
   ..., `Arch E3`.

 - **JIS A and B Series**: As defined by the Japanese Industrial Standards
   (JIS). e.g. `JB0`, ..., `JB12`.

 - **Shiroku Ban and Kiku**: The following 5 sizes are available: `Shiroku ban
   4`, `Shiroku ban 5`, `Shiroku ban 6`, `Kiku 4`, `Kiku 5`.

The exact size of these constants (plus some history and background) can be
found on [papersizes.io](https://papersizes.io).


### `orientation`

| Property       | Value  |
|:---------------|:-------|
| Type           | String |
| Required       | ❌     |
| Default        | `null` |
| Case-sensitive | ❌     |

A string, which describes the orientation of the page: `"portrait"`,
`"landscape"`, or `null`.

```json
{
  "page": {
    "size": "A4",
    "orientation": "landscape"
  }
}
```

 - When `landscape`, the calculated width and height of the page will be
   swapped if and only if `height > width`.
 - When `portrait`, the calculated width and height of the page will be swapped
   if and only if `width > height`.
 - When `null`, no swapping will occur.


### Padding and Margins

> Margins create extra space around an element. In contrast, `padding` creates
> extra space *within* an element.  
> — [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/CSS/margin)

The above snippet describes the difference between the CSS properties `margin`
and `padding`. In print/typography however, we typically use the term *margin*
to refer to spacing *within* the page, which is in direct contrast to the
definition laid out by CSS. Because of this discrepancy, we need to lay out
some rules to determine the ground truth.

When the CSS property `margin` is used to style a page, treat it as `padding`
instead.

```json
{
  "page": {
    "margin": "2.8cm 4cm"
  }
}
```

The above example JSON would be described in CSS as follows:

```css
.page {
  padding: 2.8cm 4cm;
}
```

The CSS property `padding` is treated as invalid, and should be ignored.


## Style Classes

Classes are enumerated within a single JSON object, where the keys are unique
and identify a single class.

```json
{
  "h1": {
    "display": "Heading 1",
    "styles": {
      "color": "#333",
      "font-size": "2rem",
      "margin": "4rem 0 2rem"
    }
  },
  "h2": {
    "display": "Heading 2",
    "styles": {
      "color": "#444",
      "font-size": "1.2rem",
      "margin": "3rem 0 2rem"
    }
  }
}
```


### `display`

| Property | Value  |
|:---------|:-------|
| Type     | String |
| Required | ✔️      |

A *human readable* string, which can be shown to users.

```json
{
  "fig": {
    "display": "Figures & Captions",
    "styles": {}
  }
}
```


### `styles`

| Property | Value  |
|:---------|:-------|
| Type     | Object |
| Required | ✔️      |

A list of *CSS expressions*, which are enumerated in a JSON object. Each key
contains a CSS property, and each value is a string containing a CSS value.

> **Note**: Be careful not to include a trailing semi-colon after CSS values!

```json
{
  "p": {
    "display": "Body Text",
    "styles": {
      "color": "green",
      "font-family": "Comic Sans, sans-serif",
      "font-size": "12pt",
      "margin": "2em 0"
    }
  }
}
```


### `inherit`

| Property       | Value  |
|:---------------|:-------|
| Type           | String |
| Required       | ❌     |
| Default        | `null` |
| Case-sensitive | ✔️      |

A string containing the unique ID of another class, from which to inherit
styles from.

```json
{
  "body": {
    "display": "Body Text",
    "styles": {
      "font-family": "Inter, sans-serif",
      "font-size": "12pt"
    }
  },
  "headings": {
    "display": "Headings",
    "inherit": "body",
    "styles": {
      "font-size": "2em"
    }
  }
}
```

This relationship could be described in CSS as follows:

```css
body,
.headings {
  font-family: Inter, sans-serif;
  font-size: 12pt;
}

.headings {
  font-size: 2em;
}
```
