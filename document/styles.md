# Named Styles

> Last updated 2019/07/25.


## Abstract

Named Styles defines a system of classifying and styling textual content in a
document.


## Table of Contents

 1. [Abstract](#abstract)
 2. [Glossary](#glossary)
 3. [Defining a Named Style](#defining-a-named-style)
    1. [`display` (Required)](#display-required)
    2. [`styles` (Required)](#styles-required)
    3. [`inherit`](#inherit)
 4. [File Format](#file-format)
 5. [Transportation Format](#transportation-format)
 6. [Coming Soon](#coming-soon)


## Glossary

 - **Human readable**: A string that is designed to be consumed by *any*
   possible user. Including users with no technical expertise or experience.
 - **CSS expression**: A CSS property-value pair. e.g. `color: red;`.


## Defining a Named Style

Named styles are enumerated within a single JSON object. The keys in this object
are used to uniquely identify each named style, which are also JSON objects.

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


### `display` (Required)

The `display` key defines a *human readable* string, which will be shown to
users choosing from possible named styles. For example:

```json
{
  "fig": {
    "display": "Figures & Captions",
    "styles": {}
  }
}
```


### `styles` (Required)

The `styles` key defines a list of *CSS expressions*, which should be applied to
any text content with the given named style. CSS expressions are enumerated in a
JSON object, where the keys contain a CSS property, and the values are CSS
values.

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

The `inherit` key gives the unique ID of another named style, from which to
inherit styles from. This allows you to setup a *cascade* effect — where
changing the value of one named style, causes all inheriting named styles to
also be updated.

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

This would result in the following CSS:

```css
.body,
.headings {
  font-family: Inter, sans-serif;
  font-size: 12pt;
}

.headings {
  font-size: 2em;
}
```


## File Format

When storing named styles in file format, place all named styles within a single
JSON file called `styles.json`. This file should be in the root directory of the
document archive.


## Transportation Format

When sending named styles over a HTTP 1.1 connection, only a single file can be
included in an HTTP response. As such, named styles may be delivered in
*transportation format*. 

In transformation format, named styles should be included as a single JSON
object, as seen in the example below:

```json
{
  "foo": { ... },
  "bar": { ... },
  "styles": {
    "body": {
      ...
    }
  }
}
```



## Coming Soon

 * Styles (other than named styles, such as page styles)
 * Wrapping
