---
description: A basic introduction to KDF metadata.
---

# Introduction to Metadata

> _Metadata is data that provides information about other data._  
> — [Wikipedia \(Metadata\)](https://en.m.wikipedia.org/wiki/Metadata)

Kauri uses document metadata for a number of reasons, each aimed at improving the user's experience. Some metadata is used for statistical purposes, such as tracking the total amount of time spent editing a document. Other metadata is used to help readers learn more about a document, such as the title, and list of contributors. The following sample shows what a typical `meta.json` might look like:

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
  "editDuration": "P3Y6M4DT12H30M5S"
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
**Note**: There are no restrictions on what data can be stored in `meta.json`. There are however a few required fields, that will be explored on the next page.
{% endhint %}

