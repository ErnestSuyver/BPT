# Workflow

## from BPT

The idea is to convert BPT into some other format, for example:

- HTML for publication on the web
- TEI for exchange and archiving purposes
- PDF for print or e-readers
- epub for e-readers

## to BPT

An important purpose of BPT is to make texts uniform. This is especially useful when working with multiple authors and editors, and/or in multiple formats.

This also means that texts from word processors or other text editors needs to be converted _into_ BPT. Given the variety input-side this will often required manual correction, preferably by the authors themselves.

## BPT converter

Conversion is done automatically, i.e with a Python script. Of course the result is checked and can be changed or corrected manually.

In the heart of the pipeline sits the [BPT converter](https://gitlab.com/brillpublishers/code/bpt-converter). The pipeline produces artifacts (in this case, CTS compliant TEI XML files) which can be examined and downloaded from the jobs page in the data repo. The repo's pipeline badge indicates the status of the pipeline and links to the pipelines page of the data repo. This feedback gives the data team a tool for quality control.

## Automation

Data is managed in git. Every commit triggers a pipeline (in GitLab), leading to publication on dev. Publication to production is manual. This is done on purpose: a last check.

CI/CD

GitLab / GitHub actions; devops

## division of labour

This set-up allows a division of labour.

1. a data team is responsible for the content
2. a dev team is responsible for the pipeline and publication in print or online
