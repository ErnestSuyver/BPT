## BPT Brill-Specific

There is a need in Brill texts to go beyond vanilla Markdown. Below a few Brill-specific extensions are listed.

### Language and script
 * **md**: `~|ἄνδρα μοι ἔννεπε, μοῦσα|~grc-Grek`
<!--  * **epidoc**: `<foreign xml:lang="grc-Grek">ἄνδρα μοι ἔννεπε, μοῦσα</foreign>` -->

### Direction
* **md**: `~|הלך אבא לעבודה|~rtl`

### Language and script and direction
* **md**: `~|~|הלך אבא לעבודה|~he-Hebr|~rtl`

It probably makes sense to indicate the base directionality and lang-script combination in a comment at the top of a work, i.e between `<!-- -->`, and to indicate in the text itself *only the exceptions*. This prevents redundant markup. 

In the bpt+2tei.py, we'll include rules like:
* not included in the base directionality (unless it is ltr) are line numbers
* not included in the base directionality (unless it is ltr) are note numbers

### Bibliography
* references are in YAML using CSL field names
* citations are in `author_year` format (acting as citekey)

### Illustrations
* Vanilla Markdown has `![foo](/url "title")`which results in HTML `<img src="/url" alt="foo" title="title" />` 
* This is just one of [many](https://github.github.com/gfm/#images) possibilities, by the way.
* Still, this system doesn't work for cases where the image descrption is very long, has multiply paragraphs and contains markup. This is the case in Brill325, for example. 
* In such cases, we place the description in a separate tag, like so `<=.ill_FILENAME DESCRIPTION =>`. For example:

```
![](01-00.jpg)

<=.ill_01-00.jpg Around 1750 Samuel Luchtmans I commissioned this allegorical mantelpiece painting from the artist Nicolaas Reyers. For many years it decorated the home of the Luchtmans family on the Rapenburg, and it now hangs in the offices of Brill. The painting shows Pallas Athena with her shield and lance, accompanied by Hermes with his winged helmet and herald’s staff. In the foreground three naked little boys are playing with prints depicting periwigged gentlemen, presumably Leiden professors.
```

### Tables

Tables are plain markdown. 

We use [this](https://github.com/thephpleague/commonmark-ext-table) CommonMark extension to add **captions** to tables. 

(See also [here](https://talk.commonmark.org/t/tables-in-pure-markdown/81/84) and [here](https://github.github.com/gfm/#tables-extension-) ).

#### Example

```md
| First Header  | Second Header | Third Header         |
| :------------ | :-----------: | -------------------: |
| First row     | Data          | Very long data entry |
| Second row    | **Cell**      | *Cell*               |
| Third row     | Cell that spans across two columns  ||
[Table caption, works as a reference][section-mmd-tables-table1]
```

### anchors
See the section on references

### table of contents

This is the thing: https://github.com/jonschlinkert/markdown-toc

###see also

* https://stackoverflow.com/questions/11948245/markdown-to-create-pages-and-table-of-contents
* https://python-markdown.github.io/extensions/toc/
* https://github.com/yzhang-gh/vscode-markdown
* https://michelf.ca/projects/php-markdown/extra/#spe-attr
* https://stackoverflow.com/questions/9721944/automatic-toc-in-github-flavoured-markdown
