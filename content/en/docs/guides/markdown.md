---
title: "Markdown"
description: ""
lead: ""
date: 2023-01-03T23:07:02-08:00
lastmod: 2023-01-03T23:07:02-08:00
draft: false
images: []
menu:
  docs:
    parent: ""
    identifier: "markdown-7ab9703e09e3ecc2ad78a0e3a6f5217f"
weight: 999
toc: true
---

## Basic Markdown Syntax

| style           | Syntax                               |
| --------------- | ------------------------------------ |
| H1              | `# Heading 1`                        |
| H2              | `## Heading 2`                       |
| H3              | `### Heading 3`                      |
| Bold            | `**Bold text**`                      |
| Bold            | `__Bold text__`                      |
| Underline       | `*underlined text*`                  |
| Underline       | `_underlined text_`                  |
| Block quote     | `> block quote`                      |
| Code            | `code`                               |
| Horizontal rule | `---`                                |
| Link            | `[text](example.com)`                |
| Image           | `![alt text](example.com/image.jpg)` |

### Headings

```
# Heading 1
## Heading 2
### Heading 3
```

### Bold and Italics

```
**Bold text**
__Bold text__

*italics text*
_italics text_
```

### Block Quote

Block quotes are intended for quotations but can be used for callouts to make to a visual distinction.

```
> Block quote
```

> Block quote

### Horizontal Rule

```
---
```

---

### Lists

#### Ordered Lists

```
1. First Item
1. Second Item
  1. Sub Item
1. Third Item
```

1. First Item
1. Second Item
   1. Sub Item
1. Third Item

#### Unordered Lists

```
- First Item
- Second Item
  - Sub Item
- Third Item
```

- First Item
- Second Item
  - Sub Item
- Third Item

### Links

**Link to External Sites**

Link to another website.

```
[display text](https://example.com)
```

**Link to Internal Pages**

Link to another page using the relative directory.

```
[display text](../relative/file/path.md)
```

**Link to Heading on Page**

Link to a heading on the same page (heading reference must be all lowercase).

```
[display text](#heading-text-all-lowercase)
```

### Images

```
[alt text](https://example.com/image.jpg)
[alt text](../assets/image.jpg)
```

## Markdown Extended Syntax

Markdown is extended with

### Emphasis

| style         | Syntax                 |
| ------------- | ---------------------- |
| Strikethrough | `~~Stikethough text~~` |
| H2            | `## Heading 2`         |

~~test~~

### Strikehrough

```
Normal text ~~strikethrough text~~
```

Normal text ~~strikethrough text~~

### Footnotes

```
This sentence contains a footnote. [^1]

[^1]: Here's the footnote.
```

### Emoji

```
Great story bro! :joy:
```

Great story bro! :joy:

### Task List

```
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media
```

Depending on the flavor of markdown, different interpreters

```
- [ ] Some require bullets and space
[ ] Bullets are not always required
[] Some require a space between brackets
```

### Tables

```
| Head | Head |
| ---- | ---- |
| Cell | Cell |
| Cell | Cell |
```

### Heading ID

```
## Some Heading {#custom-header-id}
```

### Highlight

```
Normal text ==highlighted text==.
```

### Subscript and Superscript

#### Subscipt

```
CO~2~
```

#### Superscipt

```
H^0^
```
