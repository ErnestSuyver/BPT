# BPT Basic

_Brill Plain Text_ (BPT) is [Markdown](https://en.wikipedia.org/wiki/Markdown) supplemented by text-edition-specific extensions.

Markdown is not a single and strictly-defined entity. Several flavours of Markdown exist, such as [CommonMark](https://commonmark.org/), [Scholarly MarkDown](http://scholmd.org/), [GitHub Flavored MarkDown](https://guides.github.com/features/mastering-markdown/), and of course the [original Markdown](https://daringfireball.net/projects/markdown/). The difference is in the extensions.

Markdown is *simple* to use. Anyone who has ever written an email has probably written in Markdown without knowing it. Remember those asterisks people use to `**stress**` something? That's Markdown. You can learn it in [60 seconds](https://commonmark.org/help/).

BPT uses Markdown as a _semantic_ format, i.e. to mark _meaning_ rather than representation. For example, in BPT we use underscores to `_emphasise_` text and asterisks to mark `**important**` text. The decision about how to render these marks is taken elsewhere, for example in the script that creates a PDF from BPT files.

This is similar to how HTML uses `<em>` to tag emphasized text instead of `<i>`, and `<strong>`to define important text instead of `<b>`. Indeed, Markdown was conceived in 2004 by John Gruber as a "text-to-HTML conversion tool for web writers." For this reason, any HTML tag is valid Markdown.

## Basic Markdown

There is no need to repeat here what has been explained clearly elsewhere. 

See [this cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) for an excellent overview of basic Markdown syntax.

For some hand-on experiences, follow [this](https://programminghistorian.org/en/lessons/getting-started-with-markdown) lesson. Highly recommended!

## Escapes

Sometime you will see things like `\<` or `\|` in the markdown. A backslash is positioned before a character. This is called " escaping". Its purpose is to enforce a certain interpretation of the escaped character. For example, a human editor may use `<` and `>` to indicate a dubious or supplemented reading of a text. However, the software processing the markdown will interpret these characters as tag markers, like `<p>`. The backslash tells the software to ignore the character.
