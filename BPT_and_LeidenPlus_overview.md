# Leiden+

## background

The text editions in _Jacoby Online_ - inscriptions, payri, even manuscripts - require precision in order to establish and convey the contributors' readings. That precision comes in the form of the [Leiden+](http://papyri.info/docs/leiden_plus) tag set.

A list of the most common sigla for the Leiden Conventions are as follows:

|||
|---|-------------| 
|ạḅ	|Letters unclear, or imperfectly preserved or executed, ambiguous without consideration of context.|
|...	|Illegible letters, not restored by the editor (extent known or approximately known, one dot per letter). Above example: three illegible letters. In some conventions, numbers between two dashes may be used for extended areas, instead of individual dots; in this case, approximation may be expressed with plus-minus sign (±) replacing the first dash, or "c." or circa before the number.|
|[...]	|Letters missing, not restored by the editor (extent known or approximately known, one dot per letter). Above example: three letters missing. In some conventions, numbers between two dashes may be used for extended areas, instead of individual dots; in this case, approximation may be expressed with plus-minus sign (±) replacing the first dash, or "c." or circa before the number.|
|[ or [ ] or ]	|Letters missing, not restored by the editor, extent unknown.|
|[abc]	|Letters missing, restored by the editor.|
|⟨ ⟩ or ***	|Letters erroneously omitted by the text, not restored by the editor.|
|⟨abc⟩	|Letters erroneously omitted by the text, restored by the editor.|
|a(bc)	|Abbreviation in the text, expanded or resolved by the editor. Doubtful expansion should be expressed with a question mark before the closing parenthesis: a(bc?).|
|{abc}	|Letters considered erroneous and superfluous by the editor. If illegible, an individual letter is expressed by a single dot each. Doubtful letters are marked by a subscript dot.|
|⟦abc⟧	|Rasura: a deletion which can be restored. In this example, the letters abc were deleted, but are still legible or can be restored from context. Deletions may alternatively be specified in the apparatus.|
|\abc/	|Interlinear addition of letters in the text itself. In this example, the letters abc were added between lines. These sigla are used when interlinear text is otherwise difficult to represent as such typographically.|

No sigla were suggested for corruptions (i.e. letters that are legible or restorable, but not understood). Instead, it was proposed that these should be dealt with in an apparatus.
No sigla were suggested for literary corrections. Instead, it was proposed that these should be dealt with in an apparatus or in a commentary.

Contributors are encouraged to use Leiden+. After all, reading a text is an academic task and the use of Leiden is an established convention in Classics. In cases where it is not possible or feasible for contributors to add Leiden+, Brill copy editors will add the tags, always in dialogue with the contributors and/or editors. 

For a full overview of the Leiden+ tag set, see the [documentation](http://papyri.info/docs/leiden_plus). Below follows a "Leiden+ cheat sheet" with four of the most widely used tags. 

## Leiden+ cheat sheet

### Document division

Say you have a papyrus consisting of two parts, A and B. Tag as follows in Leiden+

```
<D=.A.part 
1. line of text
2. line of text 
 =D> 
<D=.B.part 
1. line of text
2. line of text
 =D>
```

Idem for columns, e.g. `<D=.i.column<=`

Note that the opening tag (`<D=.1`) has a space after it. Likewise, the closing tag (`=D>`) has a space before it.

Note: do **not** do something like `<D=.1.1.part` , as `1.1` signifies **two** levels in the CTS hierarchy, whereas the Leiden+ division marker creates **one** level. (Of course, tags can be nested to create a hierarchy). 

### Line numbers

Say you have a papyrus with a text in lines. Tag as follows in Leiden+

```
1. a line of text
2. another line of text
3. you get the picture
```

### Words that wrap across lines

Say you have a papyrus with a text in lines and there is a word on the end of one line and it breaks off and it is continued at the beginning of the next line. Tag as follows in Leiden+

```
1. word word wordbegin
2.- wordend word word
```

Note: the hyphen must be written at the start of the following line. Then a space. Then the rest of the word.

### Character space range
Say you have a papyrus with a text in lines and there is a gap in a line. It’s between 3 and 5 characters. Tag as follows in Leiden+

```
vac.3-5
```

Note: if it’s exactly three, do `vac.3`. If it’s around three, do `vac.ca.3`.

#### Documentation

Full documentation: http://papyri.info/docs/leiden_plus

Bit of background: https://wiki.digitalclassicist.org/Leiden-plus

LeidenMark. A markdown extension for converting texts with Leiden+ to TEI Epidoc XML: https://pypi.org/project/leidenmark/


<!-- 
## Papyri

Some fragments in _JO_ consist of papyrus texts. This occurs mainly in IV, but also in other parts (I, for example, and V). These texts often, if not always, are submitted to Brill devoid of any papyrological mark up. In other words, they contain no [Leiden](https://en.wikipedia.org/wiki/Leiden_Conventions).

This can be problematic in cases where a certain repesentation of a papyrus text is required but there are no markers to peg the rendering on. Moreover, one can question how serious a text edition is if the main papyrological standard is not used.

Ideally, Leiden is added to the papyrus texts in _JO_. In particular, this should take the form of [Leiden+](http://papyri.info/docs/leiden_plus), which is a set of normalized and standardized Leiden markers.

However, adding Leiden+ is a big job. We need to discuss with the editors

* if and how we want to do it for _existing_ entries
* what we should do in the case of _new_ entries: compel authors to use Leiden?

The above also applies to inscription texts.
-->
