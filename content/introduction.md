---
description: Introduction to content.json
---

# Introduction

Kauri represents the contents of a document as a tree, where the root node is the document itself, and child nodes represent the various types of nodes and elements which make up a document's contents. You can find this tree inside `content.json`.

{% code-tabs %}
{% code-tabs-item title="content.json" %}
```javascript
[
  {
    "type": "heading",
    "level": 1,
    "class": "h1",
    "styles": { "color": "blue" },
    "children": ["Let's Break Conventions"]
  },
  {
    "type": "paragraph",
    "class": "body",
    "children": ["Dare to be different."]
  }
]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Elements

Elements are defined by a single JSON object, containing each of the following keys:

| Key | Purpose |
| :--- | :--- |
| `"type"` | Determines the type of element, such as `"heading"`, `"image"` or `"table"`. If you where writing HTML, this would be the tag name. A list of [all available element types ](elements/)is available on the following page. |
| `"class"` | An optional style class. |
| `"styles"` | An optional list of KCSS expressions, which apply only to this element. These styles will always take precedence over the styles inherited from an element's class. You can view a list of all [available KCSS styles here](../styles/kcss.md). |
| `"children"` | A list of child elements. |

Some element types may also require additional keys.

