# Nodes

## Text

Text nodes can be used in place of other elements. They may not have styles, classes, or children. Instead, they must have a `"content"` key.

```javascript
{
  "type": "text",
  "content": "Hello world!"
}
```

You may also use a single string as shorthand:

```javascript
{
  "type": "paragraph",
  "children": ["The quick brown fox jumped over the lazy dog."]
}
```

## Breaks

There two main types of break in KDF documents.

### Line breaks

Line breaks allow you to insert a carriage return, moving content to the next line.

```javascript
{
  "type": "paragraph",
  "children": [
    "Hooray!",
    { "type": "lineBreak" },
    "—Dr. Zoidberg"
  ]
}
```

{% hint style="info" %}
**Note**: A line break should never be used to separate two paragraphs of content. Instead, they should be represented as separate paragraph elements.
{% endhint %}

### Page Breaks

Page breaks let the page layout engine know to insert a manual page break.

```javascript
[
  {
    "type": "heading",
    "children": ["Page 1"]
  },
  { "type": "pageBreak" },
  {
    "type": "heading",
    "children": ["Page 2"]
  }
]
```

