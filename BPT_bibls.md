# Bibliographic data in BPT

## Terminology

First, a terminological point: we disintuish between inline _citations_ and end-of-text _references_.

### Citations

* Citations point to a specific place/passage in a work (either in a primary source or in secundary literature)
* Citations are short, e.g. "Johnson 2018, p. 3"
* Citations occur in the base text (the running text) of a scholarly article or chapter

### References

* The term "bibliographies" can refer to either a list of references that go with a scholarly article or chapter, or to a specialized type of scholarly publication
* References in bibliographies give full bibliographical data (author, title, year of publication, DOI, etc.)
* Bibliographies may contain (sub) headings, like "Primary sources", "Reference works", etc.
* Bibliographies may contain abbreviations of publications, often in list or table-like structures
* Bibliographies may contain annotations
* Bibliographies are ordered (alphabetically on title, e.g., or chronologically)
* In print publications, references may sit in (foot) notes, or at the end/back of a chapter/article, as a separate "bibliography"

## Citations in BPT

A citation in BPT is a _combination_ of _citekey_ and place. 

For example `@West_2020 pp. 34-45`

In this example `@West_2020` is the citekey and `pp. 34-45` is the place, the location in the referred work. The location is free. The citekey is restricted:

* The  _citekey_ is an identifier that connects citation and reference. It must be identical to the value in the ID filed of the reference (see below), minus the `a` sign
* It is a combination of `@ + [author name] _ [publication year]`. If West published two works in 2020, we write `2020a` and `2020b`.

## References in BPT

There is a definition of the mandatory and optional fields per publicartion type. It can be found [here](https://gitlab.com/brillpublishers/code/zotero_brill/-/blob/master/documentation/Mappings.xlsx).

Here is an example

```
- author:
  - family: Zimmerman
    given: B.
  container-title: Brill's New Pauly
  container-title-short: BNP
  id: Zimmerman2004
  issued:
  - year: 2004
  publisher-place: Leiden
  title: Euphantus
  type: entry-encyclopedia
  volume: 5
```

All references in BPT sit in a _bibl block_:


```

```bibl

[bunch of references]

\`\`\`

```


A bibl block may occur anywwhere within a textpart.

## CSL YAML

Brill uses _YAML format_ and _CSL fields_ for its bibliographies.

YAML basically consists of pairs of _keys_ asnd _values_. See the [official site](https://yaml.org/) for more information. Also check this [linter](http://www.yamllint.com/).

CSL stands for Citation Style Language. It is used for styling (_not_ a concern in BPT) but in order to style, it defines semantic elements. These are the keys in BPT references. See the [official site](https://citationstyles.org/) for more information. 


## pointers and anchors

How to create pointers and anchors in BPT?

### Pointers

This is a pointer: 

`see the [Biographical Essay](#Biographical-Essay) below.` 

Note that the anchors can have no upper case and no spaces; replace them by hyphens.

In this example, the header (in Markdown, of course) is `# Biographical Essay`. This gets transformed into an HTML ID that acts as anchor. Is this mechanism sufficiently generic and robust?

### Anchors

In the example above, the anchor is created automatically in the transformation from MarkDown into HTML. Or you might say that the MarkDown header acts as anchor.

What if there is no header? In those chose, a dedicated anchor is created. This is done as follows:

* the phrase is placed between `##` like so: `## Phrase that needs anchor ##`. 

This is (in Pandoc Markdown) an alternative way of writing a head, and so makes uses of the md2html mechanism described above.

The pointer in this example is `#phrase-that-needs-anchor`.

## Markup in bibliographic data

What to do if a title contains text in italics or superscript? We use the following tags:

* italics: `_ _`
* bold: `** **`
* superscript: `^ ^`

