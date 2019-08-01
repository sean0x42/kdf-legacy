# Page Styles

The `page` styles JSON object, contains zero or more key-value pairs, which describe the appearance of each page. You may use any valid CSS expression, or one of the custom style expressions described in the sections below.

## `size`

| Property | Value |
| :--- | :--- |
| Type | String |
| Required | ❌ |
| Default | `"A4"` |
| Case-sensitive | ❌ |

A string, containing a _page size constant_. A default value of `A4` is assumed when no value is given.

```json
{
  "page": {
    "size": "Letter"
  }
}
```

The CSS properties `height` and `width` will always take precedence over the `size`, effectively overriding it within one axis. Consider the following JSON snippet:

```json
{
  "page": {
    "size": "A4",
    "height": "100mm"
  }
}
```

This page could be described with the following CSS:

```css
.page {
  height: 100mm; /* Overrides 297mm */
  width: 210mm;
}
```

### **Page Size Constants**

The following page size constants are currently available for use \(more may be added in future\):

* **A and B Series**: As defined by ISO 216.
* **C Series**: As defined by ISO 269.
* **Common US Loose Sizes**: The following four sizes are available: `Letter`, `Legal`, `Tabloid`, and `Ledger`.
* **US ANSI Series**: As defined by ANSI/ASME Y14.1 and Y14.1M.
* **US ARCH Series**: As defined by ANSI/ASME Y14.1 and Y14.1M.
* **JIS A and B Series**: As defined by the Japanese Industrial Standards \(JIS\).
* **Shiroku Ban and Kiku**: The following 5 sizes are available: `Shiroku ban 4`, `Shiroku ban 5`, `Shiroku ban 6`, `Kiku 4`, `Kiku 5`.

The exact size of these constants \(plus some history and background\) can be found on [papersizes.io](https://papersizes.io).

## `orientation`

| Property | Value |
| :--- | :--- |
| Type | String |
| Required | ❌ |
| Default | `null` |
| Case-sensitive | ❌ |

A string, which describes the orientation of the page: `"portrait"`, `"landscape"`, or `null`.

```json
{
  "page": {
    "size": "A4",
    "orientation": "landscape"
  }
}
```

* When `landscape`, the calculated width and height of the page will be

  swapped if and only if `height > width`.

* When `portrait`, the calculated width and height of the page will be swapped

  if and only if `width > height`.

* When `null`, no swapping will occur.

## Padding and Margins

> Margins create extra space around an element. In contrast, `padding` creates extra space _within_ an element.
>
> — [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/CSS/margin)

The above snippet describes the difference between the CSS properties `margin` and `padding`. In print/typography however, we typically use the term _margin_ to refer to spacing _within_ the page, which is in direct contrast to the definition laid out by CSS. Because of this discrepancy, we need to lay out some rules to determine the ground truth.

When the CSS property `margin` is used to style a page, treat it as `padding` instead.

```json
{
  "page": {
    "margin": "2.8cm 4cm"
  }
}
```

The above example JSON would be described in CSS as follows:

```css
.page {
  padding: 2.8cm 4cm;
}
```

The CSS property `padding` is treated as invalid, and should be ignored.

