# BPT Other matters

### Escapes

Sometime you will see things like `\<` or `\|` in the markdown. A backslash is positioned before a character. This is called " escaping". Its purpose is to enforce a certain interpretation of the escaped character. For example, a human editor may use `<` and `>` to indicate a dubious or supplemented reading of a text. However, the software processing the markdown will interpret these characters as tag markers, like `<p>`. The backslash tells the software to ignore the character.

### Newlines

[Newlines](https://en.wikipedia.org/wiki/Newline) are control characters in a character encoding specification like Unicode that signify the end of a line of text and the start of a new one. Several such characters exist. Some of the most widely used are:

```
 CR = carriage return (return to beginning of line) = Macintosh before OSX
 LF = line feed (= move down one line) = Unix, macOS
 CR LF = a combination of LF and CR = Windows
```

The Unicode points for these characters are (in hexadecimal notation):

```
 CR = U+000D
 LF = U+000A
 CR+LF = U+000D followed by U+000A
```

In certain programming languages, these control characters are handled by escape sequences. In Python, for example, `\r` represents a carriage return, and `\n` a line feed. Other languages may have different escape sequences to set, search and replace special characters. The following therefore only applies to BPT:

```
 CR = U+000D = \r
 LF = U+000A = \n
 CR+LF = U+000D U+000A = \r\n
```
