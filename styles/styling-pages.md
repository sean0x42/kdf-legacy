# Styling Pages

{% hint style="info" %}
**Note**: There is presently no way to have different styles for different pages. If there is sufficient demand for such a feature however, we could add more fine control in future.
{% endhint %}

The `page` JSON object, allows you to define a series of styles which apply to the pages in your document. You may notice that Kauri style expressions are reminiscent of CSS expressions

## Size

`size` is an optional string property, which allows you to use one of the many supported [page sizes](page-sizes.md). A default value of `"A4"` is assumed when no value is given.

{% page-ref page="page-sizes.md" %}

```javascript
{
  "page": {
    "size": "A4"
  }
}
```

The CSS properties `height` and `width` will always take precedence over the `size`, effectively overriding it within one axis. Consider the following JSON snippet:

```javascript
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

## Orientation

The optional `orientation` property describes whether pages in this document should be rendered as `"portrait"`, `"landscape"`, or `"inferred"`. The default value is `"inferred"`, where the orientation is determined based on the page's width and height.

```javascript
{
  "page": {
    "size": "A4",
    "orientation": "landscape"
  }
}
```

## Margins

`margin` is an optional property, which defines the amount of spacing between the edge of the document's content area, and the side of the page. The example below uses the `margin` shorthand, but the following properties are also available—and typically encouraged unless you're editing the styles by hand:

* `marginTop`
* `marginBottom`
* `marginLeft`
* `marginRight`

```javascript
{
  "page": {
    "margin": "2.8cm 4cm"
  }
}
```

This would be represented by the following CSS:

```css
.page {
  padding: 2.8cm 4cm;
}
```

{% hint style="info" %}
Note that we use the [typographic definition of margin](https://en.m.wikipedia.org/wiki/Margin_%28typography%29) here, rather than the [CSS definition](https://developer.mozilla.org/en-US/docs/Web/CSS/margin). Typographic margin is closer to CSS's padding.
{% endhint %}

## Other

The following [KCSS expressions](kcss.md) are also available for use in page styles:

* Background
* Borders

{% page-ref page="kcss.md" %}

