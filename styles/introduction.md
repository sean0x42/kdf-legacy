# Introduction

Styles are composed in JavaScript Object Notation \(JSON\), and are contained within a single, root JSON object with the following keys:

* `page` – A JSON object, which defines the appearance of each page.
* `classes` – A JSON object, which enumerates all available style classes.

For example:

{% code-tabs %}
{% code-tabs-item title="styles.json" %}
```yaml
{
  "page": {
    "size": "A4",
    "orientation": "portrait",
    "margin": "2cm 3cm"
  },
  "classes": {
    "fig": { }
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

