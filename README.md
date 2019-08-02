---
description: A quick introduction to the Kauri Document Format.
---

# Welcome

## Introduction

{% hint style="danger" %}
**Warning**: This specification is still a draft, and is liable to change at any time. Kauri Document Format is presently a working title, and thus may change name in future.
{% endhint %}

The following is a pseudo-technical specification which defines and discusses the Kauri Document Format \(KDF\). KDF is a [JSON](https://json.org) based file format, which can be used to describe an editable document. It was designed for use alongside the desktop document processor [Kauri](https://github.com/sean0x42/kauri), and enables the following unique features:

* [ ] Shared colour palettes
* [ ] Persistent edit history
* [ ] Persistent clipboard history
* [ ] Document versioning
* [ ] Document level dictionary
* [ ] And more to come...

## Motivation

There are already a number of existing, open document formats available today. So it may not be immediately obvious why another document format is required—especially since it's good practice to reuse existing standards and specifications wherever possible. 

![https://xkcd.com/927/](.gitbook/assets/standards.png)

To understand our motivations behind KDF, you first need to understand the primary motivation that drives development of Kauri:

> Document processors have become bound by their own conventions. So much so, that innovation and creativity is suffocated. Kauri should never be afraid of breaking conventions, and challenging what we've come to consider as normal—so long as there is some measurable benefit to the user's experience.

There's nothing inherently wrong with the existing formats, but they lack one thing that Kauri really needs: flexibility. We need a document format that let's us define a basic set of rules, and makes few assumptions about what kind of features those rules enable. In essence, KDF is more of a template that enables us to experiment and be creative, than a precise technical specification.

