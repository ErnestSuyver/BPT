# Workflow

### from BPT

The idea is to convert BPT into some other format, for example:

- HTML for publication on the web
- TEI for exchange and archiving purposes
- PDF for print or e-readers
- epub for e-readers

### to BPT

An important purpose of BPT is to make texts uniform. This is especially useful when working with multiple authors and editors, and/or in multiple formats.

This also means that texts from word processors or other text editors needs to be converted _into_ BPT. Given the variety input-side this will often required manual correction, preferably by the authors themselves.

### BPT converter

Conversion is done automatically, i.e with a Python script. Of course the result is checked and can be changed or corrected manually.

In the heart of the pipeline sits the [BPT converter](https://gitlab.com/brillpublishers/code/bpt-converter). The pipeline produces artifacts (in this case, CTS compliant TEI XML files) which can be examined and downloaded from the jobs page in the data repo. The repo's pipeline badge indicates the status of the pipeline and links to the pipelines page of the data repo. This feedback gives the data team a tool for quality control.

### Automation

The BPT converter is a script. Likewise, other moments in the workflow may be automated, e.g. checking the validity of the BPT or other formats, or checking the well-functioning of an online application.

Plain text can be version-managed with git. Environments like GitLab or GitHub also make it possible to automate the workflow as a whole, in a so-called _pipeline_. An edit in a document could, via a commit, lead to a triggering of the workflow and so, for example, to an immediate change online.

However, it makes sense to check things manually, certainly before publishing entire texts online.

### division of labour

A set-up like this allows a division of labour.

1. a data team is responsible for the content
2. a dev team is responsible for the pipeline and publication in print or online

<!-- 
Brill's [workflow](https://brillpublishers.gitlab.io/documentation-workflow/) for creating, editing, and publishing content is based on plain text. This means that whatever the source format, the content is converted into plain text. The plain text is processed, enriched, and converted into other formats for publication, exchange, or archiving.

The selected plain text format is [MarkDown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet), supplemented by some text-edition-specific extensions. Hence the name _Basic Plain Text_, or BPT for short.

BPT supports the inclusion of additional mark-up, such as [Leiden+]() for epigraphical texts, [YAML]() for metadata and references, and [HTML]().

After conversion to plain text, the content may be further processed. For example, it can be copy-edited, indexed, and converted into TEI XML for publication on Brill's [Scholarly Edition site](https://labs.brill.com/se/). 

By default, such processes are automated and take place in GitLab, which not only is the version control system, but acts as the entire pipeline for this workflow.
-->