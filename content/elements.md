# Elements

This section lists all available KDF elements in alphabetical order.


## `blockQuote`

A `blockQuote` allows you to clearly outline an extract from another source. e.g.

> ...we show how a 19hz standing air wave may under certain conditions create sensory phenomena suggestive of a ghost...  
> —_Vic Tandy & Tony R. Lawrence, 1998. [The Ghost in the Machine](http://www.richardwiseman.com/resources/ghost-in-machine.pdf)_

```javascript
{
  "type": "blockQuote",
  "children": [
    "...we show how a 19hz standing air wave may under certain conditions create sensory phenomena suggestive of a ghost...",
    {
      "type": "blockQuoteAttribution",
      "children": [
        "Vic Tandy & Tony R. Lawrence, 1998. ",
        {
          "type": "hyperlink",
          "href": "http://www.richardwiseman.com/resources/ghost-in-the-machine.pdf",
          "children": ["The Ghost in the Machine"]
        }
      ]
    }
  ]
}
```

## `blockQuoteAttribution`

The `blockQuoteAttribution` element must be a top level child of a `blockQuote` element. It gives proper attribution to the author, or authors, of external content. For example usage, see [`blockQuote`](#blockquote).



## `caption`

The `caption` element is used to label images, tables, and other block content.

```javascript
{
  "type": "image",
  "source": "resource://images/red-tailed-black-cockatoo.png",
  "alt": "A red tailed black cockatoo.",
  "children": [
    { "type": "caption", "children": ["A red tailed black cockatoo."] }
  ]
}
```

{% hint style="info" %}
Captions are the only valid children of an image.
{% endhint %}




## `code`

Inline `code` provides no syntax highlighting—although the user may add their own emphasis by adjusting the appearance of the text.

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


## `codeBlock`

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


### `language`

The `language` attribute defines the programming language that is used within the code block. Doing so allows the syntax highlighting engine to apply the correct formatting. If no `language` is defined, a value of`"plain text"` is assumed.


### `lineNumbers`

The optional `lineNumbers` attribute determines whether line numbers should be drawn. If the attribute is not defined, then line numbers are shown, unless the code block is only one line tall.


### `fileName`

The optional `fileName` attribute adds the name of the file at the top of the code block. 



## `heading`

A simple section `heading`.

```javascript
{
    "type": "heading",
    "level": 1,
    "styles": {},
    "children": ["Conclusion"]
}
```

### `level`

The required `level` attribute contains an integer from 1 to 6, defining the heading's heirarchical level.


## `hint` (Callout)

The `hint` element, also known as a callout, is a simple block element with a little more visual interest than typical body text.

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

### `variant`

The `variant` attribute may be any of the following:

| Value | Description |
| :--- | :--- |
| `"information"` | A blue hint, with an info icon. |
| `"success"` | A green hint, with a success icon. |
| `"warning"` | An orange hint, with a warning icon. |
| `"error"` | A red hint, with an error icon. |





## `hyperlink`

Hyperlinks allow document authors to link to external content. Hyperlinks are not restricted to web-based documents, and may use any valid protocol, such as:

* `https:`
* `http:`
* `mailto:`
* `file:`
* etc.

```javascript
{
  "type": "link",
  "title": "My website",
  "href": "https://seanbailey.io",
  "children": ["seanbailey.io"]
}
```

### `title`

The `title` attribute is an optional string, which will display when hovering the cursor over the link.


### `href`

The `href` attribute contains the full URI to the external content.




## `image`

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




## List

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



## List Item

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


## `paragraph`

Basic body text. Paragraphs do not have any special attributes.

```javascript
{
  "type": "paragraph",
  "class": "body",
  "styles": {},
  "children": ["All their equipment and instruments are alive."]
}
```


## `span`

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

## `table`

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

## `tableCell`

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

## `tableRow`

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

## `tableColumnGroup`

The optional column group element contains only columns as children. It allows you to apply styles to all cells within the defined columns. This is mostly used as an optimisation technique, to prevent duplicate inline styles appearing on every cell in a column.

## `tableColumn`

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
