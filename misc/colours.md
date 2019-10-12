---
description: Specification for colours.json
---

# Document Colours

Document level colour palettes are a must have for any creative software. They allow users to define and name custom shades, to re-use throughout the document.

```json
{
  "cosmic-blue-500": "#3647E2",
  "cosmic-blue-400": "#4857E4",
  "cosmic-blue-300": "#5A68E7",
  ...
}
```

Other elements throughout the document may reference these colours, rather than hardcoding their value.

```json
{
  "type": "span",
  "styles": {
    "color": "$cosmic-blue-500"
  },
  "children": ["Look, I'm Cosmic Blue 500!"]
}
```
