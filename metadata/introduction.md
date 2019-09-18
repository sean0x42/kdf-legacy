---
description: Introduction to meta.json
---

# Introduction

> _Metadata is data that provides information about other data._  
> — [Wikipedia \(Metadata\)](https://en.m.wikipedia.org/wiki/Metadata)

`meta.json` is a simple key-value store, that developers can use to store all kinds of additional data about a document. Whilst there are no required fields, there are however a few standard fields that any document can reasonably be expected to contain. These fields are explored on the following page.

{% code-tabs %}
{% code-tabs-item title="meta.json" %}
```javascript
{
  "title": "Let's Rethink Document Processing",
  "authors": [
    "Sean Bailey",
    "Adam Crocker",
    "Prajna Sariputra",
    "Luke Ingram",
    "David Abraham"
  ],
  "createdAt": "2019-08-01T12:59:15+11:00",
  "updatedAt": "2019-08-01T12:59:15+11:00",
  "editDuration": "P3Y6M4DT12H30M5S",
  "kdfVersion": "1.0"
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

