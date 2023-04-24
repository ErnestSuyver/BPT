# BPT for Text Editions

## Introduction
The following is a _supplement_ to the document [BPT Basic Guidelines](BPT_Basic_Guidelines.html) that provide basic guidelines for handling Brill publications in plain text format, particularly MarkDown with some Brill-specific extensions. This document presupposes working knowledge of these guidelines.

This document does _not_ say anything about previous or subsequent steps in the workflow. It does not, for example, detail what a text edition should look like in a rich text format like MS Word. Nor does it say anything about a structuring format like TEI XML.

This document does _not_ say anything about what a Brill text edition should look like, either in print or online. Questions of rendering are decided in consultation with the authors or editors. 

Text editions are manyfold in their approach and can be quite complex. The aim of the Brill workflow that puts plain text in central place is to reduce that complexity, and to give different matters a separate place in a workflow. The creation of XML or the rendering of a publication are examples. 

Complexity can be added by subsequent phases of the workflow, where each phase is handled by scripts. The purpose of the BPT script is to produce a text editon consisting of a base text and one or more sets of annotations in plain text. Its focus is on clarity and consistency.

Complexity and exceptions will no doubt arise, and will be dealt with when we get there. In some cases that may lead to changes in this document. The aim of the following is not to cater for all cases, but to be used. 

## Unicode and font
BPT requires that all text is in Unicode, encoded in UTF-8. The Brill font is mandatory. In cases where a script is not included in the Brill font, another font may be used in comnsultation with [Brill's script expert](mailto:rietbroek@brill.com). The list of currently used fonts is found [here](waar ook al weer?).

## Base Text

### Lines
BPT defines _line beginnings_ and _line ends_. A line beginning is indicated by a line line. A line end is indicated by the absence of any characters after the last one on a line. 

Authors are responsible for clearly indicated line beginnings and line ends.

In many plain text editors, pressing the ENTER key ends a line and starts a new line. This normally results in a U+000A, visible as the beginning of a new line.

For BPT, only the the presence of the Unicode point U+000A is decisive. Any other Unicode point is replaced (using the BPT script) by it.

#### Example
```
first line
second line
```

### Line numbers
BPT requires line numbers (if required) to be preprended to _all_ lines. (This does not mean they are rendered as such in the publication). 

Authors are responsible for clearly indicated line numbers, for example at every line, or every fifth line. THe BPT script converts these to all lines.

Line numbers are entered by adding a number, followed by a full stop and a space.

The Unicode points are U+0031 (or any other number), U+002E, and U+0020. Any other Unicode point is replaced (using the BPT script) by these.

#### Example
```
1. first line
2. second line
```

### Appendix on Newlines
Newlines are control characters in a character encoding specification like Unicode that signify the end of a line of text and the start of a new one. Several such characters exist. Some of the most widely used are:

 CR = carriage return (return to beginning of line) = Macintosh before OSX
 LF = line feed (= move down one line) = Unix, macOS
 CR LF = a combination of LF and CR = Windows

The Unicode points for these characters are (in hexadecimal notation):

 CR = U+000D
 LF = U+000A
 CR+LF = U+000D followed by U+000A

In certain programming languages, these control characters are handled by escape sequences. In Python, for example, `\r` represents a carriage return, and `\n` a line feed. Other languages mnay have different escape sequences to set, search and replace special characters. The following therefore only applies to BPT:

 CR = U+000D = \r
 LF = U+000A = \n
 CR+LF = U+000D U+000A = \r\n

See [Wikipedia](https://en.wikipedia.org/wiki/Newline).

### Page numbers
If we use BPT to digitize print editions, we may be faced with the need to deal with what [TEI](https://tei-c.org/release/doc/tei-p5-doc/en/html/CO.html#CORS5) calls "milestone elements", i.e. markers of the non-logical structure of a text, such as page numbers of a particular edition. 

[Leiden+](https://brillpublishers.gitlab.io/documentation-seg/LeidenPlus-complete.html#document-div) can help us here: it has markers for blocks of text and divisions like recto/verso (`<=` and `<=.r` respectively). (Note that the milestone elements are all closed, whereas the Leiden+ markers open and close). This system can be combined with that of TEI to form the following:

TEI | explanation | BPT
----- | ----- | -----
`<milestone>` | a boundary point | `<=.ms pindakaas =>`
`<gb>` | gathering beginning | `<=.gb pindakaas =>`
`<pb>` | page beginning | `<=.pb pindakaas =>`
`<lb>` | line beginning | `<=.lb pindakaas =>`
`<cb>` | column beginning | `<=.cb pindakaas =>`

The space that is now occupied by the non-sensical term `pindakaas` can be used to specify the editon or give additional information.

Note, by the way, that the marker for line beginning is superfluous as we already have `1. first line`.

#### Example
```
1. first<=.pb Migne 456 => line
2. second line
3. third<=.ms GNO page 123  => line
4. fourth line
```

## Critical apparatus

### Critical apparatus as notes
BPT regards a critical apparatus as a form of annotation, in this case, on the base text, and therefore uses _notes_ to represent text-critical remarks. In particular, stand-off notes are used, that is, the notes are not included in the base text, but _separated_ from it. The separation consists of one blank line.

#### Example
```
1. line one of base text[^1]
2. line two of base text[^2]

[^1] first text-critical remark
[^2] second text-critical remark
```

If the base text is provided by the author in parts, the BPT script will join them. (At least untill the time that DTS and CapiTainS allow for works that don't consist of a single file). If the critical apparatus is also provided in parts, the BPT script will join them.

### Connecting base text and critical apparatus
BPT uses the vanilla MarkDown system of note numbers. The point in the base text is marked with `[^1]`, for example. This same marker is found at the beginning of the text-critical remark, followed by a space and the body of the remark, like so: `[^1] text-critical remark`.

BPT requires notes to be uniquely identified per base text.

Te example above shows an annotation marker for a _point_ in the base text. How to mark a _span_? By the addition of an extra marker that indicates the beginning of the span, like so: `^span of text[^1]`.` This is a BPT extension of vanilla MarkDown. (Overlapping spans are not allowed).

Note identifiers need not be numbers. They can be anything, except spaces, tabs, or newlines.

### Multiple apparatuses
How to deal with multiple apparatuses? By adding an identifier for each apparatus to its note numbers. 

So, if a text has, for example, both text-critical and historical annotations, i.e. a critical apparatus and "ordinary" notes, then these could be labelled A and B respectively. The first annotation of the apparatus criticus would be marked `A1`, etc. 

#### Example
```
1. line one of base text[^A1]
2. line two of ^base text[^A2]
3. line ^three[^B1] of base text[^A3]
4. line four of base text[^B2]

[^A1] first text-critical remark
[^A2] second text-critical remark
[^A3] third text-critical remark

[^B1] first historical remark
[^B2] second historical remark
```

### Text-critical remarks
What does the body of a text-critical remark look like?

BPT expects a scholarly edition of a text to record some or all of the known variations among different witnesses to the text. The critical apparatus contains information about these variant readings of the text in highly structured form.

Each note groups together all readings, i.e. all variations for a word or phrase in the text, per witness.

An example: the first three lines of the _Prologue_ to Chaucer's _Wife of Bath_. There are four manuscripts for this text, and for three of them a variant reading of the first line may be recorded like this:

#### Example
```
1. Experience, though noon auctoritee[^1]
2. Were in this world, is right ynogh for me
3. To speke of wo that is in mariage;

[^1] El Experience though noon Auctoritee; La Experiment thouh noon Auctoritee; Ra2 Eryment though none auctorite.
```

The BPT script places the manuscript marker before the variant reading (separated by a space). Any markup (e.g., italics) is removed. Individual variations are separated by a semi-colon. 

A note, i.e. an apparatus entry, may contain a lemma, i.e. a reading accepted as that of the original or of the base text. This may look as follows:

#### Example

```
1. Experience[^1], though[^2] noon auctoritee
2. Were in this world, is right ynogh for me
3. To speke of wo that is in mariage;

[^1] El Hg **Experience**; La Experiment; Ra2 Eryment
[^2] El Ra **though**; La thouh
```

The lemma is marked in bold; this can be done by the BPT script because the word or phrase appears exactly like that in the base text. 

### List of Witnesses

The above requires a unique identifier for each witness. BPT expects scholarly editions to provide a list of witness and their markers (sometimes known as 'sigla').

The BPT script places the list of witnesses between base text and critical apparatus. It may look as follows:

#### Example

```
El = Ellesmere, Huntingdon Library 26.C.9
Hg = Hengwrt, National Library of Wales, Aberystwyth, Peniarth 392D
La = British Library Lansdowne 851
Ra2 = Bodleian Library Rawlinson Poetic 149
```

## Marginalia

There are several types, e.g.

* References to other editions (often following the physical structure, e.g. Migne pages, Whiston sections, etc.)
* Some explicatory or summary annotation

Such marginalia should be attached to (clean, free of anchors and such like) base text via URNs, but these have no place in human-readable BPT. What to do? Treat them like notes.

#### Example

```
Ἔστι μὲν καὶ πᾶσιν ὑαῖν τοῖς τὴν ἰατρικὴν αετιοῦσι[^1]

[^1] 71 Merc.
```

In this example it is unclear if the annotation refers to to the wordl or to the line. Disambiguate as follows:

#### Example

```
1.[^1] Ἔστι μὲν καὶ πᾶσιν ὑαῖν τοῖς τὴν ἰατρικὴν αετιοῦσι

[^1] 71 Merc.
```

*There is currently no way to indicate a wider or more narrow span than the line. (But see my BNJ example!!!)*

Using different sets of annotation, for example, critical apparatus combined with commentary notes and marginal notes, requires a way to disambiguite, i.e to mark each system as such. Use simple markers to do so, e.g. letters, like so:

#### Example

```
1.[^1] A line[^2] of base text[^3]

[^1] MN A marginal note
[^2] AC A text-crtical note
[^3] CN A commentary note
```

It does not matter which markers are used, as long as they are clear and used consistently.

## Milestones

* If the logical structure of a work differs from the physical structure, Brill uses [milestone elements](https://brillpublishers.gitlab.io/documentation-tei-xml/page_numbers.html) in the TEI XML to indicate the physical structure.
* In BPT, such milestone elemements are indicated as follows: `<=.UNIT NUMBER=>`. for example, in ETTO, we use:

```
•	Physical structure: Van der Valk: tome <=.vt [tome number] =>; page <=.vp [page number] =>; line <=.vl [page number] =>. These are “closed “elements; place them at the start of the text they structure.
•	Physical structure: Rome: tome <=.rt [tome number] =>; page <=.rp [page number] =>; line <=.rl [line number] =>. These are “closed “elements; place them at the start of the text they structure. The markers for the Rome line numbers replace the vertical lines (pipe symbols) that now occur in the base text at every five Rome lines.
```

* PS. At this moment, the difference between logical (`<div>`, `<ab>`) and physical (`<milestone>`, `<pb>`, `<lb>`) is not strictly enforced. We really should do this.
