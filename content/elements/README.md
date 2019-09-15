# Elements

This section lists all available KDF elements in alphabetical order.

## Block Quote

The `blockQuote` element allows you to clearly outline an extract from another source. e.g.

> ...we show how a 19hz standing air wave may under certain conditions create sensory phenomena suggestive of a ghost...  
> —_Vic Tandy & Tony R. Lawrence, 1998._ [_The Ghost in the Machine_](http://www.richardwiseman.com/resources/ghost-in-machine.pdf)

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

## Block Quote Attribution

The `blockQuoteAttribution` element must be a top level child of a `blockQuote` element. It gives proper attribution to the author, or authors, of external content. For example usage, see [`blockQuote`](./#block-quote).

## Caption

The `caption` element is used to label images, tables, and other block content. Note that captions must be included as immediate children of the block element they are captioning.

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

## Code

The inline `code` element provides no syntax highlighting—although the user may add their own emphasis by adjusting the appearance of the text.

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

## Code Block

The `codeBlock` element allows document authors to show a larger portion of their code, and make full use of syntax highlighting for supported languages.

```javascript
{
  "type": "codeBlock",
  "language": "ruby",
  "lineNumbers": true,
  "fileName": "players_controller.rb",
  "children": ["# Paginated list of players\ndef index\n  @players = Player.order(score: desc).page(params[:page])\nend"]
}
```

The above markup would render a code block that looks something like this:

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

### `language`: string

The `language` attribute defines the programming language that is used within the code block. Doing so allows the syntax highlighting engine to apply the correct formatting. If no `language` is defined, a value of`"plain text"` is assumed.

### `lineNumbers`: boolean

The optional `lineNumbers` attribute determines whether line numbers should be drawn. If the attribute is not defined, then line numbers are shown, unless the code block is only one line tall.

### `fileName`: string

The optional `fileName` attribute adds the name of the file at the top of the code block.

## Counter

The `counter` element is used to automatically number repeating elements in a document. They are commonly used for numbering headings, images and tables. 

```javascript
{
  "type": "heading",
  "level": 2,
  "children": [
    { "type": "counter", "use": "headings" },
    "Designing for designers"
  ]
}
```

Assuming that the `headings` counter template is defined as `"{parent?}{counter:decimal}."`, the above markup would produce the following content:

```text
1.3. Designing for designers
```

### `use`: string

The `use` attribute contains the unique identifier of a [counter template](counter-templates.md).

### `depth`: integer \(Optional\)

The optional `depth` attribute defines the counter's nested depth. Note that this attribute can be inferred when the counter is an immediate child of a [heading](./#heading) element, based on the heading's level.

## Heading

A simple section `heading`.

```javascript
{
    "type": "heading",
    "level": 1,
    "styles": {},
    "children": ["Conclusion"]
}
```

### `level`: integer

The required `level` attribute contains an integer from 1 to 6, defining the heading's heirarchical level.

## Hint

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

### `variant`: string

The `variant` attribute may be any of the following:

| Value | Description |
| :--- | :--- |
| `"information"` | A blue hint, with an info icon. |
| `"success"` | A green hint, with a success icon. |
| `"warning"` | An orange hint, with a warning icon. |
| `"error"` | A red hint, with an error icon. |

## Hyperlink

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

### `title`: string

The `title` attribute is an optional string, which will display when hovering the cursor over the link.

### `href`: string

The `href` attribute contains the full URI to the external content.

## Image

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

A bulleted or numbered `list`, which enumerates zero or more `listItem`s. Sample markup follows.

```javascript
{
  "type": "list",
  "bullet": { "variant": "filledBullet" },
  "children": [
    { "type": "listItem", "children": ["One fish"] },
    { "type": "listItem", "children": ["Two fish"] },
    { "type": "listItem", "children": ["Red fish"] },
    { "type": "listItem", "children": ["Blue fish"] }
  ]
}
```

After rendering this list, you would get something like the following:

```text
• One fish
• Two fish
• Red fish
• Blue fish
```

### `bullet`: Object

{% hint style="info" %}
**Note**: The term _bullet_ is used interchangeably throughout this section to refer to both bullets and numbering.
{% endhint %}

The `bullet` attribute defines the appearance of the list's bullets or numbering. A bullet must have one—and only one—of the following attributes:

| Attribute | Description |
| :--- | :--- |
| `char` | A single Unicode character. e.g. `'>'` |
| `variant` | One of the many available variants. See [Numbering Variants](bullets-and-numbering.md#numbering-variants) and [Bullet Variants](bullets-and-numbering.md#bullet-variants). |
| `image` | A resource URI which points to an image |

If a bullet is not defined for a list, then the document renderer will search for an appropriate [bullet cycle](./#bulletcycle), and use the matching bullet definition.

#### `prefix`: char

The `prefix` attribute defines a single Unicode character that will appear before the bullet.

```javascript
{
  "variant": "lowerLatin",
  "prefix": "-"
}
```

```text
-a Each letter in this list is immediately prefixed by a '-' character.
-b You can use the prefix attribute in conjunction with the suffix attribute...
-c ...to create some interesting looking bullets.
```

#### `suffix`: char

The `suffix` attribute defines a single unicode character that will appear after the bullet.

```javascript
{
  "variant": "decimal",
  "suffix": "."
}
```

```text
1. A dot is added to each list item
2. Thanks to the suffix attribute.
```

#### `startIndex`: integer

A non-negative integer \(&gt;= 0\), defining where numbering for an ordered list should begin.

```javascript
{
  "variant": "decimal",
  "suffix": ".",
  "startIndex": 5
}
```

```text
5. First item
6. Second item
```

### `bulletCycle`: Array&lt;Object&gt;

Nested lists follow a sequence called a _bullet cycle_, where each level of nesting moves one position further in the cycle. When the end is reached, the current bullet wraps around to the beginning again.

```text
{
  "type": "list",
  "bulletCycle": [
    { "variant": "lowerRoman", "suffix": "." },
    { "variant": "lowerGreek", "suffix": "." },
    { "variant": "filledBullet" }
  ],
  "children": [...]
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

The `bulletCycle` attribute applies to all nested lists, unless a nested list has defined its own `"bullet"`—in wich case that list will ignore the overall cycle.

## List Item

A `listItem` element represents a single entry within a larger `list`.

```javascript
{
  "type": "list",
  "bullet": { "variant": "lowerLatin", "suffix": "." },
  "children": [
    {
      "type": "listItem",
      "children": ["Hello world!"]
    }
  ]
}
```

### `bullet`: Object

The optional `bullet` attribute allows a list item to override the bullet of its parent `list`.

```javascript
{
  "type": "listItem",
  "bullet": {
    "char": "*",
    "suffix": "."
  },
  "children": ["Red fish"]
}
```

## Paragraph

The `paragraph` element contains body text.

```javascript
{
  "type": "paragraph",
  "class": "body",
  "styles": {},
  "children": ["All their equipment and instruments are alive."]
}
```

## Span

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

## Table

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

## Table Cell

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

## Table Row

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

## Table Column Group

The optional column group element contains only columns as children. It allows you to apply styles to all cells within the defined columns. This is mostly used as an optimisation technique, to prevent duplicate inline styles appearing on every cell in a column.

## Table Column

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

