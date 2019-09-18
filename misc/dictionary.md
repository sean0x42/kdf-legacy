---
description: Specification for dictionary.json
---

# Dictionary

There are many circumstances in which a user may wish to add their own words to
the spell check dictionary. Consider each of the following edge cases:

 * Proper nouns which start with a lower case letter. This typically only occurs
   with brand names.
 * Jargon.
 * Invented words, such as product names.
 * Words and phrase from other languages.
 * Onomatopoeia. e.g. ZAAAAAAAAAAAAAAAAAAAP.
 * Industry standard misspellings. See [HTTP Referer](https://en.wikipedia.org/wiki/HTTP_referrer).
 * Unsupported language variations. E.g. Many Australians are already used to
   adding *colour*, *metre*, *organise*, *analogue*, etc. to our spell check
   dictionaries when `English (Australia)` is not available.
 * A word is missing from the standard dictionary for some other reason.

A document level dictionary, stored in `dictionary.json`, attempts to resolve
this issue at the document level. It contains a single JSON array of strings,
where each string is another word that the user can add to the spell check
dictionary.

{% code-tabs %}
{% code-tabs-item title="dictionary.json" %}
```javascript
["Snuffleupagus", "referer", "Git"]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

