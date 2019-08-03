---
description: This page outlines which fields are required for a valid meta.json file.
---

# Required Fields

## Title

Every document must have a `"title"`. The title should be a human readable string, which can be shown to both document authors and readers. 

{% code-tabs %}
{% code-tabs-item title="meta.json" %}
```javascript
{
  "title": "15 Reasons Comic Sans is the World's Greatest Font",
  ...
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Authors

The `"authors"` metadata field, contains an array of strings, listing the names of each person that contributed. 

{% code-tabs %}
{% code-tabs-item title="meta.json" %}
```javascript
{
  "title": "On Colour and Brand Identity",
  "authors": ["Sean Bailey"],
  ...
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Timestamps

A number of important timestamps should be included in each document's metadata, such as the date of creation, and last modification. All timestamps must conform to the [ISO 8601 standard](https://www.iso.org/iso-8601-date-and-time-format.html). [Wikipedia](https://en.m.wikipedia.org/wiki/ISO_8601) provides a good summary of the specification for those in a rush.

### Created At

Time of document creation.

{% code-tabs %}
{% code-tabs-item title="meta.json" %}
```javascript
{
  ...,
  "createdAt": "2019-08-03T02:37:12+11",
  ...
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Last Modification

Time that the document was last written to. If a document is opened, but it's contents are not changed, then this value will not be updated.

{% code-tabs %}
{% code-tabs-item title="meta.json" %}
```javascript
{
  ...,
  "updatedAt": "2019-08-03T02:37:12+11",
  ...
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Edit Duration

The total amount of time spent editing the document. Implementations are only expected to be accurate to the second.

{% hint style="info" %}
**Note**: Durations are also represented in accordance with the ISO 8601 standard. See [Durations](https://en.m.wikipedia.org/wiki/ISO_8601#Durations) section \(ISO 8601 Wikipedia\).
{% endhint %}

{% code-tabs %}
{% code-tabs-item title="meta.json" %}
```javascript
{
  ...,
  "editDuration": "PT12H30M5S",
  ...
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

