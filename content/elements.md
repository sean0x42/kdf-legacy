# Elements

This section lists all available KDF elements in alphabetical order.


## Block Quote

A block quote allows you to clearly outline an extract from another source.

> ...we show how a 19hz standing air wave may under certain conditions create sensory phenomena suggestive of a ghost...  
> —_Vic Tandy & Tony R. Lawrence, 1998. [The Ghost in the Machine](http://www.richardwiseman.com/resources/ghost-in-machine.pdf)_

You can create a blockquote with the following markup:

```javascript
{
  "type": "quote",
  "children": [...]
}
```



## Caption

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


## Code Block

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





## Heading

A simple section heading. You must also define the heading `"level"`, which should be an integer from 1 to 6.

```javascript
{
    "type": "heading",
    "level": 1,
    "styles": {},
    "children": ["Conclusion"]
}
```




## Hint (Callout)

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





## Hyperlink

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




## `list`

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

```
• One fish
• Two fish
• Red fish
• Blue fish
```

### `bullet`

{% hint style="info" %}
**Note**: The term _bullet_ is used interchangeably throughout this section to refer to both bullets and numbering. 
{% endhint %}

The `bullet` attribute defines the appearance of the list's bullets or numbering. A bullet must have one—and only one—of the following attributes:

| Attribute | Description |
| :--- | :--- |
| `char` | A unicode character. e.g. `'>'` |
| `variant` | One of the many available variants. See [Numbering Variants](/content/bullets-and-numbering#numbering-variants) and [Bullet Variants](/content/bullets-and-numbering#bullet-variants). |
| `image` | A resource URI which points to an image |

If a bullet is not defined for a list, then the document renderer will search for an appropriate [bullet cycle](#bulletcycle), and use the matching bullet definition.


#### `prefix`

The `prefix` attribute defines a single unicode character that will appear before the bullet.

```javascript
{
  "variant": "lowerLatin",
  "prefix": "-"
}
```

```
-a Each letter in this list is immediately prefixed by a '-' character.
-b You can use the prefix attribute in conjunction with the suffix attribute...
-c ...to create some interesting looking bullets.
```

#### `suffix`

The `suffix` attribute defines a single unicode character that will appear after the bullet.

```javascript
{
  "variant": "decimal",
  "suffix": "."
}
```

```
1. A dot is added to each list item
2. Thanks to the suffix attribute.
```


#### `startIndex`

A non-negative integer (>= 0), defining where numbering for an ordered list should begin.

```javascript
{
  "variant": "decimal",
  "suffix": ".",
  "startIndex": 5
}
```

```
5. First item
6. Second item
```


### `bulletCycle`

Nested lists follow a sequence called a _bullet cycle_, where each level of nesting moves one position further in the cycle. When the end is reached, the current bullet wraps around to the beginning again.

```
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



## `listItem`

A `listItem` represents a single entry within a larger `list`. 

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

### `bullet`

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

Basic body text. Paragraphs do not have any special keys.

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

### Table Column

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
