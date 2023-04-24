# BPT in the wild

## Who uses BPT?

Brill Academic Publishers was the launching customer of BPT. Many of the publications on its text editions platform  _Brill Scholarly Editions_ use BPT. For example, all publications that are updated regularly, such as the flagship products _Jacoby Online_ and _SEG Online_ use BPT to create and edit new content.

Of course, there are many other projects out there that use plain text that is then converted into some other format, like TEI. For example [Papyri.info]() or [OpenITI](https://alraqmiyyat.github.io/OpenITI/). See the beginning of this documentation.

### Lessons learned

Brill Academic Publishers  has been using the BPT format since 2019. Two major lessons were learned in that time.

1. Authors are used to work in rich text, **with** mark up, like you see in word processors. Many reject plain text as ugly or computer-like. Editors struggle with the separation of concerns and the exactitude required by the format.
2. Text editions can be quite complex. In those cases, BPT can become quite complex as well. As complex as the TEI you are trying to avoid, but which you are basically duplicating. The advantage of simplicity and human readability is much reduced.

It is not so simple to mitigate this. An appeal to open science and GDPR may counter the users' aversion to plain text, but it is ratio versus emotion. I guess we need better tools to help people work in plain text, tools that support rich text.

Regarding the second lesson: BPT differs from TEI in one respect: its commitment to stand-off annotation. Only very recently (2022) did TEI introduce stand-off annotation. Traditionally, TEI documents cram _all_ information into a single document. This does not help with readability.

(Of course, there are other arguments why BPT might trump XML, such as the fact that XML is brittle,verbose, and unsuitable for publication on the web).
