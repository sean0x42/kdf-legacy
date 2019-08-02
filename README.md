# Welcome

{% hint style="danger" %}
**Warning**: This specification is still a draft, and is liable to change at any time. Kauri Document Format is presently a working title, and thus may change name in future.
{% endhint %}

The following is a pseudo-technical specification which defines and discusses the Kauri Document Format \(KDF\). KDF is a [JSON](https://json.org) based file format, which can be used to describe an editable document. It was designed for use alongside the desktop document processor [Kauri](https://github.com/sean0x42/kauri), and enables the following unique features:

* [ ] Shared colour palettes
* [ ] Persistent edit history
* [ ] Persistent clipboard history
* [ ] Document versioning
* [ ] And more to come...

## Motivation

There are already a number of existing, open document formats, so why should we make an entirely new document format just for Kauri? Especially when we consider the following comic from XKCD author Randall Munroe. two major existing document formats that are prevalent today:

![https://xkcd.com/927/](.gitbook/assets/standards.png)

* _Open Document Format \(ODF\)_ – An XML based document format favoured by open source document processors like LibreOffice and Apache OpenOffice.
* _Office Open XML \(DOCX\)_ – An XML based document format primarily used by Microsoft Word. The technical specification is over 5000 pages long.

There's nothing inherently wrong with the aforementioned formats, but they lack one thing that Kauri really needs: extensibility. We need a document format that let's us define a basic set of rules, which we can then build on top off, and easily add features at the document level in future.

Who is the target audience of this spec? 

Much like the IntelliJ IDEA project format, it's not meant to be an open standard that all document processors understand how to parse and edit. But rather, it's just meant to allow us to iterate and make changes as necessary, and easily add features that don't exist in other formats.

