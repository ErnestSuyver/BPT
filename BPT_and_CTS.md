# BPT and CTS

### Background

At its heart, CTS is an ontology of text. Text as a tree structure, work as versions. BPT can  be used in a CTS compliant way. This means that the ontology is expressed in BPT. Here is how:

### Structure

CTS structure is expressed with hashes.

siglum | explanation
---- | -----
`#` | textgroup
`##` | work
`###` | textpart
`####` | CTS version

There is another siglum, `#####`, but it denotes a header and plays no rule in the text structure.

### Versions

There are three work versions in CTS, indicated with a fixed terminology:

flavour | siglum
----- | -----
edition | `#### edition:`
translation | `#### translation:`
commentary | `#### commentary:`

### metadata

- _Textgroup_ metadata sit in a `settings.yml` or a `texgroup.md`. **this is inconsistent. Why not use YAML here too?**
- _Work_ metadata sit in a Pandoc-style YAML block at the top of a work.
- _Textpart_ metadata sit in a regular style YAML block at the top of a textpart.

For other metadata (at lower level than text parts), use stand-off annotation.

We have yet to devise a way to indicate mandatory and optional metadata fields.

### files and folder

The structure of the CTS folder is described elsewhere. Basically a folder per textgroup; within it a folder per work and an `.xml` per version. (BTW, textgroup and work have the crazy CTS xml file with metadata. These are converted from the BPT).

BPT can simply follow this: a folder per textgroup; within it a folder per work and an `.md` per version.

Likewise, CTS has requirements for file names, BPT can simply follow them.

<!-- 
## Technical details

JO uses the [BPT converter](https://gitlab.com/brillpublishers/code/bpt-converter) to convert BPT files into CTS compliant TEI XML files. This page gives the details.

### Technical details on values

* `# workgroup fgrh` => no need to put this in JO entries. The value `fgrh` is used in the CTS URN. It must be identical to the name of the folder containing the BPT files with JO entries (as well as the mandatory settings.xml and optional textgroup.md files)
* YAML field `title` is used in `<teiHeader>` and `__cts__.xml` (of work)
* YAML field `label` is used in  `__cts__.xml` (of work). The [converter](https://gitlab.com/brillpublishers/code/bpt-converter) puts `(Edition)`, `(Translation)`, or `(Commentary)` behind it
* `## work 0633` => the value `0633` is used in the CTS URN. The converter compares this name with the file name of the BPT file.
* `### edition: Banana` => the value `Banana` is used in the `<head>` of the `<div>`. This value is optional. Things like `### edition: Edition` are superfluous and can be removed.
* `texgroup.md` => optional
* `settings.yml` => required. Required fields are ...
* `#### commentary: Banana` => the value `Banana` is used to group similar commentaries into one file. This needs revision.
* The converter works within a folder. In that folder, it expects another folder containing the BPT files with JO entries (as well as the mandatory settings.xml and optional textgroup.md files). The name of that folder must be identical to the name of the textgroup as used in the CTS URN

### Technical details about metadata

 There are **mandatory** and **optional** metadata fields. Optional fields are **not** affected by the conversion process. Mandatory fields are required for the CTS files, for the folder and file names, and of course for the URNs.

It does not matter **where**in the textgroup the metadata fields occur, but in JO we place them as “high” as possible:

- textgroup metadata go in the settings YAML
- work metadata go in the .md files.

Note that you can have "textgroup.md" files, i.e. files at the level of a textgroup. These can have metadata too. But in JO, we don't use them.

It is also possible to have metadata on textpart level. But currently the script ignores it. With one exception: language. See below. 

#### Mandatory fields

 So these are the mandatory fields:

Field name | Occurs in | Example of value | Used for/in | Explanation
----- | ----- | ----- | ----- | -----
textgroup\_title (or: groupname) | settings YAML |  | CTS file (ti:groupname) | textgroup level
textgroup\_urn\_trunc | settings YAML | urn:cts:greekLit | URN | textgroup level
textgroup\_abbreviation | settings YAML | fgrh/bnj/bnj | URN | textgroup level
publication\_code | settings YAML | jo | URN | textgroup level
work\_abbreviation | .md YAML (BPT file) |  0001 | URN | work level
The string between four hashes and the colon | .md hashes (BPT file) | `#### translation: Translation` | CTS (ti:label) | work level
description | .md YAML (BPT file) |  | CTS (ti:description) | work level 
publication\_version  | .md YAML (BPT file) | 3 | URN | 
default\_language | settings YAML |  | eng | URN, CTS, TEI | textgroup level
default\_source\_language | settings YAML | grc | URN, CTS, TEI | textgroup level
source\_language | .md YAML (BPT file) | ara | TEI | work level and textpart level
editors | settings YAML _or _.md YAML (BPT file) | Worthington, Ian | TEI (`<teiHeader>`) | 
issn | settings YAML _or _.md YAML (BPT file) | 1873-5363 | TEI (`<teiHeader>`) | 
publication\_date | settings YAML _or _.md YAML (BPT file) |  | TEI (`<teiHeader>`) | 
publication\_place | settings YAML _or _.md YAML (BPT file) | Leiden - New York | TEI (`<teiHeader>`) | 
publisher | settings YAML _or _.md YAML (BPT file) | Brill | TEI (`<teiHeader>`) | 
author | settings YAML _or _.md YAML (BPT file) | Williams, Mary Frances (San Matteo, CA) | TEI (`<teiHeader>`) | 
reference\_levels | settings YAML _or _.md YAML (BPT file) | \- section: div | TEI (`<teiHeader>`) | `<refsDecl>`

Notes:

1. There is no need for a field stating “ed” or “tr” or “comm” because we retrieve this from the ti:label.
2. There is no need for a field stating the cts\_version\_number because we retrieve this simply from the amount of files.
3. The field “source\_language” does not exist yet…
4. We currently have **both** `##` title and YAML title: . This needs to be de-doubled.

#### Optional fields

These are the optional fields we have so far:

field | TEI XML |  used in
----- | ----- | -----
Publication\_statement (which sits in the md YAML at work level) |?? | ??
Subject  | ?? | ??

#### Mandatory CTS fields

These are the mandatory CTS fields. (The cpt metadata are optional CTS fields).

field | TEI XML |  used in
----- | ----- | -----
textgroup\_urn  | @urn | Textgroup cts
textgroupname | <ti:groupname> | Textgroup cts
work\_urn | @workURN | Work cts
work\_title | <ti:title> | Work cts
work\_version\_urn | @urn | Work cts
source\_language | @xml:lang | Work cts
cts\_version | <ti:edition> etc. | Work cts
label | <ti:label> | Work cts
description | <ti:description> | Work cts
Commentaar language | ?? | ??

Notes

1. In the work cts, the attribute carrying the textgroup URN is called `@groupUrn`
2. `<ti:edition>` etc. is taken care of by the converter, so need for a field.

#### Settings YAML

We need only one settings YAML per textgroup.

#### file names

BPT files names in JO are either `0001.md`, `0001_ed2.md` or `0001_ed3.md` (within the textgroup folder).

#### other

* Don’t create CTS versions at textpart level
* replace `### subsection` with `### textpart` 
* remove historian metadata from YAML table at work level and ignore this table, just like we ignore the fragment metadata.
* Add publication statement as YAML field publication\_statement:
-->

### see also
- [my documentation of CTS](https://brillpublishers.gitlab.io/documentation-cts)