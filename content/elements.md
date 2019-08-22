# Elements

This section lists all available KDF elements in alphabetical order.



## Captions

Captions may be used to label images, tables, and other block content.

```javascript
{
  "type": "caption",
  "children": ["Two-spiral task visualised with keras"]
}
```




## Code

Inline code provides no syntax highlighting—although the user may add their own emphasis by adjusting the appearance of the text.

```javascript
{
  "type": "paragraph",
  "children": [
    "You can always use the ",
    { "type": "code", "children": ["println!"] },
    " macro to print a string to the console. e.g. ",
    { "type": "code", "children": ["println!(\"Hello world\")"] }
  ]
}
```

When used in context, the above sample would look something like this:

> You can always use the `println!` macro to print a string to the console. e.g. `println!("Hello world")`.


## Code Blocks

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




## Hints (Callouts)

Hints, also known as callouts, are simple block elements with a little more visual interest than a standard paragraph, helping them to stand out against body text.

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




## Lists

A bulleted or numbered list element. 

```javascript
{
  "type": "list",
  "bulletCycle": [
    { "variant": "lowerRoman", "suffix": "." },
    { "variant": "lowerGreek", "suffix": "." },
    "filledCircle",
  ],
  "children": [
    {
      "type": "listItem",
      "children": [
        "Level 1",
        {
          "type": "list",
          "children": [...]
        }
      ]
    }
  ]
}
```

The above mark-up should produce the following list:

```text
i. Level 1
  α. Level 2 (Nested list)
    • Level 3
      i. Level 4 (Note how the bullet wraps around to beginning of the cycle)
ii. Another list item
```

### Bullet Cycle

List bullet styles follow a sequence called a _cycle_. 

List and list item element may define their own bullets, and ignore the overall cycle. 

### Bullets

Bullets are defined as either a `"variant"`...

```javascript
{
  "variant": "decimal",
  "suffix": "."
}
```

...a `"string"`...

```javascript
{
  "prefix": "[",
  "string": "•",
  "suffix": "]"
}
```

...or an `"image"`

```javascript
{
  "image": "resource://images/DUgZaK3RO1iG499.png"
}
```

Bullets may also optional have a prefix and suffix, which can contain any string.

### Numbering Variants

The following variants for an ordered list are available:

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

### Bullet Variants

The following variants are available for bullets:

| Variant | Preview |
| :--- | :--- |
| `"filledBullet"` | • A filled circle |
| `"hollowBullet"` | ◦ A hollow circle |
| `"filledSquare"` | ▪ A filled square |
| `"hollowSquare"` | ▫ A hollow square |



## List Items

List items may have their own defined bullet character/symbol. When this is specified, the custom bullet is used instead of the parent's bullet.

```javascript
{
  "type": "list",
  "bullet": { "variant": "lowerLatin", "suffix": "." },
  "children": [
    { "type": "listItem", "children": ["One fish"] },
    { "type": "listItem", "children": ["Two fish"] },
    {
      "type": "listItem",
      "bullet": {
        "string": "*",
        "suffix": "."
      },
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

Spans are simple elements which allow you to apply inline formatting to text.

{% hint style="info" %}
Document authors should never really be aware of the existence of span elements. They are simply a means of wrapping styles around text nodes.
{% endhint %}

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

## Table Cells

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

## Table Rows

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

## Table Column Groups

The optional column group element contains only columns as children. It allows you to apply styles to all cells within the defined columns. This is mostly used as an optimisation technique, to prevent duplicate inline styles appearing on every cell in a column.

### Table Columns

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
