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

