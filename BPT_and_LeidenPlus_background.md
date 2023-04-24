# BPT and Leiden+ 

### Leiden+ context

Leiden+ is a unified and consistent system of mark up signs used in the edition of epigraphical and papyrological texts. It is a renewed systematization of the [Leiden conventions](https://en.wikipedia.org/wiki/Leiden_Conventions) which had been applied increasingly idiosyncratically and erroneously in print publications. It was necessitated by the online publication of the entire corpus of Greep papyri in the [Papyri.info](https://papyri.info/) project.

- https://wiki.digitalclassicist.org/Leiden-plus | Leiden-plus

### Leiden+ in BPT

[Leiden+](http://papyri.info/docs/leiden_plus) is designed as a system of markers in plain text. For example, in Leiden+, every block of text must be enclosed in a pair fo brackets like this:

`<= ... =>`

The plain text is then converted into XML, specifically Epidoc, an extension of TEI and the de facto standard for editions of Greek and Latin epigraphical and papyrological texts.

BPT is also designed as plain text to be converted into XML. |It therrfore makes senses for BPT to support Leiden+. This means extending Markdown with the Leiden+ makers.



### example

See the [SEG Guidelines](https://brillpublishers.gitlab.io/documentation-seg) for _Supplementum Epigraphicum Graecum_ for an example of how Leiden+ is used in a Brill publication.