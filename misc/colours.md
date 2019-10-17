---
description: Specification for colours.json
---

# Document Colours

Document level colours allow users to define and name shades of colour, which all users may then reference throughout the document.

`colours.json` is used to keep track of these colours. It contains an ordered list of shades, where each shade has a unique identifier, a human readable name, and a valid colour value.

```json
[
  {
    "id": "cosmic-blue-500",
    "name": "Cosmic Blue 500",
    "value": "#3647E2"
  },
  {
    "id": "cosmic-blue-400",
    "name": "Cosmic Blue 400",
    "value": "#4857E4"
  },
  {
    "id": "cosmic-blue-300",
    "name": "Cosmic Blue 300",
    "value": "#5A68E7"
  },
  ...
]
```

To reference a defined shade, simply prefix its unique ID with a `$` symbol, as seen below.

```json
{
  "type": "span",
  "styles": {
    "color": "$cosmic-blue-500"
  },
  "children": ["Look, I'm Cosmic Blue 500!"]
}
```
