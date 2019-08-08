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

```javascript
{ "color": "hsl(240, 15%, 10%)" }
```

### Font Family

Font family

```javascript
{ "fontFamily": "Inter, sans-serif" }
```

### Font Size

Font size

```javascript
{ "fontSize": "2em" }
```

### Font Weight

Font weight

```javascript
{ "fontWeight": "bold" }
```

### Italics

Italics

```javascript
{ "italic": "true" }
```

### Letter Spacing

Letter spacing

```javascript
{ "letterSpacing": "4%" }
```

### Line Height

Line height

```javascript
{ "lineHeight": "1.5" }
```

### Spacing

```javascript
{ "spacing": "3rem 0rem" }
```

```javascript
{ "spacingTop": "2cm" }
```

### Strikethrough

Strikethrough

```javascript
{ "strikethrough": "true" }
```

### Text Align

```javascript
{ "textAlign": "left" }
```

### Text Transform

Uppercase, lowercase, sentence case, title case

```javascript
{ "textTransform": "uppercase" }
```

### Underline

underline

```javascript
{ "underline": "true" }
```

