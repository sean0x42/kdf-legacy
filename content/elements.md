# Elements

## Headings

A simple section heading. You must also define the heading `"level"`, which should be an integer from 1 to 6.

```javascript
{
    "type": "heading",
    "level": 1,
    "styles": {},
    "children": ["Conclusion"]
}
```

## Paragraphs

Basic body text. Paragraphs do not have any special keys.

```javascript
{
  "type": "paragraph",
  "class": "body",
  "styles": {},
  "children": ["All their equipment and instruments are alive."]
}
```

## Spans

Spans allow you to apply formatting to text inline, without affecting the layout of the page. Document authors should never really be aware of the existence of these elements.

```javascript
{
  "type": "paragraph",
  "class": "body",
  "children": [
    "Spans are actually ",
    {
      "type": "span",
      "styles": {
        "color": "blue",
        "underline": "true",
        "italic": "true",
        "fontWeight": "bold"
      },
      "children": ["super useful"]
    },
    " because they provide you with total control over the appearance of inline text."
  ]
}
```

## Lists

A bulleted or numbered list element. Lists must be either ordered or unordered, which affects the types of bullets that are available.

```javascript
{
  "type": "list",
  "cycle": [
    {
      "variant": "lowerRoman",
      "suffix": "."
    },
    {
      "variant": "lowerGreek",
      "suffix": "."
    },
    "filledCircle",
  ],
  "children": [...]
}
```

```javascript
i. Level 1
  α. Level 2
    • Level 3
      i. Level 4 (Wraps around)
```

### Ordered Lists

The following variants for an ordered list are available \(with potentially more to come\):

| Variant | Example |
| :--- | :--- |
| `"decimal"` | 1, 2, 3, 4, 5, 6, etc. |
| `"decimalLeadingZero"` | 01, 02, 03, 04, 05, 06, etc. |
| `"lowerRoman"` | i, ii, iii, iv, v, vi, etc. |
| `"upperRoman"` | I, II, III, IV, V, VI, etc. |
| `"lowerGreek"` | α, β, γ, δ, ε, ζ, etc. |
| `"upperGreek"` | Α, Β, Γ, Δ, Ε, Ζ, etc. |
| `"lowerLatin"` | a, b, c, d, e, f, etc. |
| `"upperLatin"` | A, B, C, D, E, F, etc. |

### Unordered Lists

Unordered lists may define either a `"variant"`, `"string"` or an `"image"`. Defining a string allows you to use an Unicode character you like as the bullet.

```javascript
{
  "type": "list",
  "ordered": false,
  "string": "×"
}
```

You may instead use any one of the following variants:

| Variant | Preview |
| :--- | :--- |
| `"filledBullet"` | • A filled circle |
| `"hollowBullet"` | ◦ A hollow circle |
| `"filledSquare"` | ▪ A filled square |
| `"hollowSquare"` | ▫ A hollow square |

Or an image/SVG, using it's resource URI:

```javascript
{
  "type": "list",
  "ordered": false,
  "image": "resource://images/DUgZaK3RO1iG499.png"
}
```

{% hint style="warning" %}
**Warning**: Resource URIs are experimental and very liable to change.
{% endhint %}

### Prefixes and Suffixes

Lists may define a `"prefix"` and `"suffix"` string if they wish, to be appended to the beginning and end of the bullet respectively. For example:

```javascript
{
  "type": "list",
  "prefix": "~",
  "suffix": "~",
  "ordered": false,
  "string": "*"
}
```

This will generate a list that looks something like this:

```text
~*~ Item one
~*~ Item two
~*~ Item three
```

### List Items

List items may have their own defined bullet character/symbol. When this is specified, the custom bullet is used instead of the parent's bullet.

```javascript
{
  "type": "list",
  "ordered": "true",
  "suffix": ".",
  "variant": "lowerLatin",
  "children": [
    { "type": "listItem", "children": ["One fish"] },
    { "type": "listItem", "children": ["Two fish"] },
    {
      "type": "listItem",
      "string": "*",
      "children": ["Red fish"]
    },
    { "type": "listItem", "children": ["Blue fish"] }
  ]
}
```

Which would produce the following effect:

```text
a. One fish
b. Two fish
*. Red fish
d. Blue fish
```

## Tables

Tables let you show information in tabular form \(a two dimensional table comprised of rows and columns\).

```javascript
{
  "type": "table",
  "children": [
    { "type": "tableRow", "children": [...] },
    { "type": "tableRow", "children": [...] },
    { "type": "tableRow", "children": [...] },
    { "type": "caption", "children": ["Eye colour by generation"] }
  ]
}
```

### Rows

The row element contains a single row of table cells.

```javascript
{
  "type": "tableRow",
  "children": [
    { "type": "tableCell", "children": [...] },
    { "type": "tableCell", "children": [...] },
    ...
  ]
}
```

### Column Groups

The optional column group element contains only columns as children. It allows you to apply styles to all cells within the defined columns. This is mostly used as an optimisation technique, to prevent duplicate inline styles appearing on every cell in a column.

#### Columns

Column elements must be contained within a `columnGroup` element, and can span zero or more columns using the `span` attribute.

```javascript
{
  "type": "tableColumnGroup",
  "children": [
    {
      "type": "tableColumn",
      "span": 2,
      "styles": { ... }
    },
    ...
  ]
}
```

### Cells

The cell element represents a single cell within a table. You can also use the optional `colSpan` and `rowSpan` attributes to have a single cell span across multiple rows or columns.

```javascript
{
  "type": "tableRow",
  "children": [
    {
      "type": "tableCell",
      "rowSpan": 2,
      "children": ["$15.00 AUD"]
    },
    {
      "type": "tableCell",
      "rowSpan": 2,
      "children": ["$15.60 NZD"]
    },
    {
      "type": "tableCell",
      "rowSpan": 2,
      "children": ["$10.20 USD"]
    },
    ...
  ]
}
```

## Images

Images are currently experimental. Here's what the mark-up may look like in future:

```javascript
{
  "type": "image",
  "viewPort": "100 0 200 0",
  "alt": "A Red-tailed Black Cockatoo (Calyptorhynchus banksii)"
  "source": "resource://images/YjTFCztRqj4QjSI.jpg",
  "children": [
    {
      "type": "caption",
      "children": ["A Red-tailed Black Cockatoo (Calyptorhynchus banksii)"]
    }
  ]
}
```

{% hint style="warning" %}
**Warning**: Resource URIs are experimental and very liable to change.
{% endhint %}

## Captions

Captions may be used to label images, tables, and other block content.

```javascript
{
  "type": "caption",
  "children": ["Two-spiral task visualised with keras"]
}
```

## Hyperlinks

Hyperlinks allow document authors to link to external content. Hyperlinks are not restricted to web-based documents, and may use any of the following protocols:

* `https:`
* `http:`
* `mailto:`
* `file:`

```javascript
{
  "type": "link",
  "href": "https://seanbailey.io",
  "children": ["seanbailey.io"]
}
```

## Code

KDF provides two main elements for representing code in your document: inline code and code blocks;

### Inline Code

Inline code provides no syntax highlighting—although the user may add their own emphasis by adjusting the appearance of the text.

```javascript
{
  "type": "code",
  "children": ["println!(\"Hello world\")"]
}
```

When used in context, the above sample would look something like this:

> You can always use the `println!` macro to print a string to the console. e.g. `println!("Hello world")`.

### Code Blocks

Code blocks allow document authors to show a larger portion of their code, and make full use of syntax highlighting for supported languages.

```javascript
{
  "type": "codeBlock",
  "language": "ruby",
  "lineNumbers": true,
  "fileName": "players_controller.rb",
  "children": ["# Paginated list of players\ndef index\n  @players = Player.order(score: desc).page(params[:page])\nend"]
}
```

Which would render a code block that looks something like this:

{% code-tabs %}
{% code-tabs-item title="players\_controller.rb" %}
```ruby
# Paginated list of players

def index
  @players = Player.order(score: :desc).page(params[:page])
end
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
**Note**: If no `"language"` is defined, `"plain text"` is assumed. This will allow users to manually apply their own formatting easily if required.
{% endhint %}

## Hints

Hints are simple block elements with a little more visual interest than a standard paragraph, helping them to stand out a little.

```javascript
{
  "type": "hint",
  "variant": "information",
  "children": [
    {
      "type": "span",
      "styles": { "fontWeight": "bold", "color": "#111" },
      "children": ["Hint:"]
    },
    " You can use hints to create heirarchy in your documents"
  ]
}
```

The following values are available for the `variant` attribute:

| Value | Description |
| :--- | :--- |
| `"information"` | A blue hint, with an info icon. |
| `"success"` | A green hint, with a success icon. |
| `"warning"` | An orange hint, with a warning icon. |
| `"error"` | A red hint, with an error icon. |

