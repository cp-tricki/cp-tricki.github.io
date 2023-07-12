---
title: About
---
![Build status](https://github.com/cp-tricki/cp-tricki.github.io/actions/workflows/ci.yml/badge.svg)

CP-Tricki is a collection of tricks for competitive programming inspired by [Tricki](https://www.tricki.org/).

## Contributing
To contribute, you can:

- Create a [pull request from fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork) (can be fully done via GitHub's web interface)
- Or, open an issue with proposed changes

## Article formatting
### Article titles
When creating a new Markdown file, specify article title via
```
---
title: Your title
---
```
Another option is to use `# Your title`, but we do not recommend it.

### Code
To insert code, use
```` 
``` c++
#include <bits/stdc++.h>
```
````
This will render as
``` c++
#include <bits/stdc++.h>
```
Specifying programming language after backticks enables code highlighting.

### Text and subheadings
To break text on the page into paragraphs, simply leave a blank line between two bodies of text.
To insert subheadings, put `## HTML h2 heading`, `### HTML h3 heading`, `#### HTML h4 heading` etc. on separate line. Using `# HTML h1 heading` is not recommended.

### Math
To add math, use `\( n^2 = -1 \)` inline. This will render as \( n^2 = -1 \). To put a formula in a separate block, use 
```
blank line
\[
\int e^x dx = e^x + C
\]
blank line
```
This will result in 

\[
\int e^x dx = e^x + C
\]

Note: GitHub's preview can display brackets incorrectly.
