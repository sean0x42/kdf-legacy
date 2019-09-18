---
description: A breakdown of the files that make up a KDF document.
---

# Archive Structure

Much like other document formats, KDF files are actually archives containing
several sub files and directories. Here's a peek into the directory structure of
a KDF file:

| File/Folder | Purpose |
| :--- | :--- |
| `resources/` | A directory that holds document resources and media, such as images, fonts, and any other static content \(work in progress\). |
| `content.json` | Contains the content and structure of your document. The headings, paragraphs, images, tables, etc. that make up your document are all defined here. |
| `colours.json` | An optional file containing the document's custom colour palette \(work in progress\). |
| `dictionary.json` | An optional file that lists any words that you've added to the project's dictionary \(work in progress\). |
| `meta.json` | Stores document metadata, such as the title and a list of authors.  |
| `styles.json` | Describes how pages and other elements in your document should look.  |

{% hint style="info" %}
**Hint**: You can check out the contents of a KDF file yourself, by changing the
file extension from `.kdf` to `.zip`, and extracting the contents of the archive
to your file system.
{% endhint %}