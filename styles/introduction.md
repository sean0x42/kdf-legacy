# Introduction

Styles are contained within a single, root JSON object with the following keys:

* `page` – A JSON object, which defines the appearance of the page.
* `classes` – A JSON object, which enumerates all available classes.

A sample `styles.json` is included below.

{% code-tabs %}
{% code-tabs-item title="styles.json" %}
```javascript
{
  "page": {
    "size": "A4",
    "orientation": "portrait",
    "margin": "2cm 3cm",
    "borderWidth": "1px",
    "borderStyle": "solid"
  },
  "classes": {
    "body": {
      "display": "Body Text",
      "styles": {
        "fontFamily": "Inter, sans-serif",
        "fontSize": "12pt",
        "color": "#333",
        "lineHeight": "1.4"
      }
    },
    "h1": {
      "display": "Heading 1",
      "inherit": "body",
      "element": {
        "type": "heading",
        "attributes": {
          "level": 1,
        }
      },
      "styles": {
        "color": "#111",
        "fontSize": "2em",
        "lineHeight": "1",
        "fontWeight": "600",
        "spacing": "4em 0 1em",
      }
    },
    {
      ...
    }
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

