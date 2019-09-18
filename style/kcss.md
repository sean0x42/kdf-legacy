---
description: A list of all available "CSS-like" style expressions.
---

# KCSS

{% hint style="danger" %}
KCSS is still experimental, and won't begin solidifying until we've created the style engine. For now, many of these properties will continue without descriptions.
{% endhint %}

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

The following is an exhaustive list of all available KCSS style properties.

### Background

The background property defines the appearance of an element's background. The background may be any of the following:

{% tabs %}
{% tab title="Colours" %}
You may use any valid [colour format](colour-and-gradients.md).

```javascript
{ "background": "#FFFFFF" }
```

{% page-ref page="colour-and-gradients.md" %}
{% endtab %}

{% tab title="Gradients" %}
You may use any valid [gradient format](colour-and-gradients.md).

```javascript
{ "background": "linear-gradient(90deg, blue, red)" }
```

{% page-ref page="colour-and-gradients.md" %}
{% endtab %}

{% tab title="Images" %}
Coming soon.

```javascript
{ "background": "resource://images/XiFasIajw58AAWs.png" }
```
{% endtab %}
{% endtabs %}

#### Size

Background size allows 

#### Repeat

Background repeat defines how background images should be repeated, if they do not fill the element.

### Borders

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

### Opacity

Opacity

```javascript
{ "opacity": "0.1" }
```

{% page-ref page="colour-and-gradients.md" %}

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

