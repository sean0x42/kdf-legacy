# Welcome

{% hint style="danger" %}
**Warning**: This specification is still a draft, and is liable to change at any time. The format is presently using a working title, and thus will change name in future.
{% endhint %}

The following is a pseudo-technical specification which defines the _Kauri Project Format_ \(KPF\). KPF is a [JSON](https://json.org) based file format, which can be used to describe an editable document project.

## Motivation

Why are these insufficient? What do we achieve by making our own project format? 

* Open Document Format \(ODF\)
* Office Open XML \(DOCX\)

Who is the target audience of this spec? 

Much like the IntelliJ IDEA project format, it's not meant to be an open standard that all document processors understand how to parse and edit. But rather, it's just meant to allow us to iterate and make changes as necessary, and easily add features that don't exist in other formats.

