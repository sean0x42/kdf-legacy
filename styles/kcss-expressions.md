---
description: A list of all available "CSS-like" style expressions.
---

# KCSS Expressions

## Introduction

Style expressions are much like [CSS expressions/declarations](https://developer.mozilla.org/en-US/docs/Web/CSS/Syntax#CSS_declarations). They contain a property and a value, but are declared in a JSON object instead:

```javascript
{
  "color": "red"
}
```

In the above example, `"color"` is the property, and `"red"` is the value.

{% hint style="warning" %}
**Warning**: Even though style expressions are almost identical to CSS expressions, the two are not interchangeable! Some CSS properties are not supported here, and some style properties are not supported in CSS.
{% endhint %}

## Available Properties

The following properties are available for use.

### Background

Set a background image, colour, or gradient.

```javascript
{ "background": "#FFFFFF" }
```

```javascript
{ "background": "resource://images/XiFasIajw58AAWs.png" }
```

```javascript
{ "background": "linear-gradient(90deg, blue, red)" }
```

### Border

Set a border.

```javascript
{ "borderWidth": "1px" }
{ "borderColor": "black" }
```

### Color

Set text colour

### Font Family

Font family

### Font Size

Font size

### Font Weight

Font weight

### Italics

Italics

### Letter Spacing

Letter spacing

### Line Height

Line height

### Spacing

```javascript
{ "spacing": "3rem 0rem" }
```

```javascript
{ "spacingTop": "2cm" }
```

### Strikethrough

Strikethrough

### Text Transform

Uppercase, lowercase, sentence case, title case

### Underline

underline

