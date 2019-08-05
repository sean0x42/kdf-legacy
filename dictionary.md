# Dictionary

{% hint style="warning" %}
**Warning:** This is an experimental file, and may not yet have any tangible effect.
{% endhint %}

`dictionary.json` contains an array of strings defined by the user, which should be included in the spell checker's dictionary. This functionality is especially useful when working on documents that repeatedly make use of unconventional jargon, invented words/product names, or even misspellings. 

{% code-tabs %}
{% code-tabs-item title="dictionary.json" %}
```javascript
["Snuffleupagus", "referer", "Git"]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

For example, imagine writing a document about HTTP headers:

> The **HTTP** **referer** \(originally a misspelling of **referrer**[\[1\]](https://en.m.wikipedia.org/wiki/HTTP_referer#cite_note-1)\) is an optional [HTTP header field](https://en.m.wikipedia.org/wiki/List_of_HTTP_header_fields) that identifies the address of the webpage...
>
> —[HTTP referer \(Wikipedia\)](https://en.m.wikipedia.org/wiki/HTTP_referer)

