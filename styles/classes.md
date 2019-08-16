# Classes

Classes are enumerated within a single JSON object, where the keys are unique and identify a single class.

```javascript
{
  "h1": {
    "display": "Heading 1",
    "element": {
      "type": "heading",
      "level": 1
    },
    "styles": {
      "color": "#333",
      "fontSize": "2rem",
      "spacing": "4rem 0 2rem"
    }
  },
  "h2": {
    "display": "Heading 2",
    "element": {
      "type": "heading",
      "level": 2
    },
    "styles": {
      "color": "#444",
      "fontSize": "1.2rem",
      "spacing": "3rem 0 2rem"
    }
  }
}
```

## Display

A required _human readable_ string, which can be shown to users.

```javascript
{
  "fig": {
    "display": "Figures & Captions",
    "styles": { ... }
  }
}
```

## Element

The optional `element` key is used to define how elements should be transformed when changing to this class. 

{% hint style="info" %}
**Note**: When defining an element, you _can not use_ either the `children` or the `class` attributes when defining the element. Otherwise, you may use any valid attributes for defining an [element](../content/elements.md).
{% endhint %}

Picture the following KDF element:

```javascript
{
  "type": "paragraph",
  "class": "body",
  "styles": {
    "fontWeight": "bold",
    "fontSize": "24px"
  },
  "children": ["Introduction to KDF"]
}
```

Now picture that the user wants to change this element to a heading, with the following class definition.

```javascript
{
  "h1": {
    "display": "Heading 1",
    "element": {
      "type": "heading",
      "level": 1
    },
    "styles": {
      "color": "#333",
      "fontSize": "2rem",
      "spacing": "4rem 0 2rem"
    }
  }
}
```

This would produce the following KDF element:

```javascript
{
  "type": "heading",
  "class": "h1",
  "level": 1,
  "children": ["Introduction to KDF"]
}
```

## Styles

A required list of [KCSS expressions](kcss.md), which are enumerated within a JSON object. 

```javascript
{
  "p": {
    "display": "Body Text",
    "styles": {
      "color": "green",
      "fontFamily": "Comic Sans, sans-serif",
      "fontSize": "12pt",
      "spacing": "2em 0"
    }
  }
}
```

{% page-ref page="kcss.md" %}

## Inherit

An optional string containing the unique ID of another class, from which to inherit styles from.

```javascript
{
  "body": {
    "display": "Body Text",
    "styles": {
      "fontFamily": "Inter, sans-serif",
      "fontSize": "12pt"
    }
  },
  "headings": {
    "display": "Headings",
    "inherit": "body",
    "styles": {
      "fontSize": "2em"
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

## Wrapping

{% hint style="warning" %}
**Warning**: Wrapping is still experimental.
{% endhint %}

```javascript
{
  "h1": {
    "display": "Heading 1",
    "wrapAfter": "avoid"
  }
}
```

