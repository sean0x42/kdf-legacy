# Classes

Classes are enumerated within a single JSON object, where the keys are unique and identify a single class.

```yaml
{
  "h1": {
    "display": "Heading 1",
    "styles": {
      "color": "#333",
      "fontSize": "2rem",
      "spacing": "4rem 0 2rem"
    }
  },
  "h2": {
    "display": "Heading 2",
    "styles": {
      "color": "#444",
      "fontSize": "1.2rem",
      "spacing": "3rem 0 2rem"
    }
  }
}
```

## `display`

| Property | Value |
| :--- | :--- |
| Type | String |
| Required | ✔️ |

A _human readable_ string, which can be shown to users.

```yaml
{
  "fig": {
    "display": "Figures & Captions",
    "styles": {}
  }
}
```



## `styles`

| Property | Value |
| :--- | :--- |
| Type | Object |
| Required | ✔️ |

A list of _CSS expressions_, which are enumerated in a JSON object. Each key contains a CSS property, and each value is a string containing a CSS value.

{% hint style="info" %}
Be careful not to include a trailing semi-colon after CSS values!
{% endhint %}

```yaml
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

## `inherit`

| Property | Value |
| :--- | :--- |
| Type | String |
| Required | ❌ |
| Default | `null` |
| Case-sensitive | ✔️ |

A string containing the unique ID of another class, from which to inherit styles from.

```yaml
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

