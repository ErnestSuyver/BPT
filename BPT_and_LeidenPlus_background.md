# BPT and Leiden+ 

### Leiden+ context

Leiden+ is a unified and consistent system of mark up signs used in the edition of epigraphical and papyrological texts. It is a renewed systematization of the [Leiden conventions](https://en.wikipedia.org/wiki/Leiden_Conventions) which had been applied inconsistently in print publications. It was necessitated by the online publication of the entire corpus of Greek papyri in the [Papyri.info](https://papyri.info/) project.

### Leiden+ in BPT

[Leiden+](http://papyri.info/docs/leiden_plus) is designed as a system of markers in plain text. For example, in Leiden+, every block of text must be enclosed in a pair fo brackets like this:

`<= ... =>`

The plain text is then converted into XML, specifically [Epidoc](https://sourceforge.net/p/epidoc/wiki/Home/), an extension of TEI and the de facto standard for editions of Greek and Latin epigraphical and papyrological texts.

BPT is also designed as plain text to be converted into XML. It therefore makes senses for BPT to support Leiden+. This means extending Markdown with the Leiden+ markers.

### example

See the [SEG Guidelines](https://brillpublishers.gitlab.io/documentation-seg) for _Supplementum Epigraphicum Graecum_ for an example of how Leiden+ is used in a prominent epigraphical publication.
