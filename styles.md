# Named Styles (Working Title)

> Last updated 2019/07/22.

## Abstract

Named Styles defines a system of classifying and styling textual content in a document.

## Glossary

 - **Human readable**: A string that is designed to be consumed by *any*
   possible user. Including users with no technical expertise or experience.

### `display`

The `display` key defines a *human readable* string, which will be shown to
users choosing from possible named styles. For example:

```json
{
  "fig": {
    "display": "Figures & Captions"
  }
}
```


## Sample

```json
{
  "paragraph": {
    "display": "Body Text",
    "styles": {
      "color": "#333",
      "font-family": "Inter, sans-serif",
      "font-size": "12pt",
      "font-weight": "400",
      "margin": "1rem 0"
    }
  },
  "heading": {
    "abstract": true,
    "inherit": "paragraph",
    "styles": {
      "color": "#222",
      "margin": "4rem 0 1rem"
    }
  },
  "heading_1": {
    "display": "Heading 1",
    "inherit": "heading",
    "styles": {
      "font-size": "2rem",
    }
  },
  "heading_2": {
    "display": "Heading 2",
    "inherit": "heading",
    "styles": {
      "font-size": "1.2rem"
    }
  },
}
```
