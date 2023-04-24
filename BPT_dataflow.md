## Data flow

This is about the data flow for which BPT is the basis.

1. the data team is responsible for the content
2. the data team is responsible for publication on dev (staging) or production

Data is managed in git. Every commit triggers a pipeline (in GitLab), leading to publication on dev. Publication to production is manual (as per usual procedure, using submodules in the SE data repo).

In the heart of the pipeline sits the [BPT converter](https://gitlab.com/brillpublishers/code/bpt-converter). The pipeline produces artifacts (in this case, CTS compliant TEI XML files) which can be examined and downloaded from the jobs page in the data repo. The repo's pipeline badge indicates the status of the pipeline and links to the pipelines page of the data repo.This feedback gives the data team a tool for quality control.