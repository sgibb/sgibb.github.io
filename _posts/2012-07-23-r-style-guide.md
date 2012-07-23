---
layout: post
title: R Code Style Guide
categories:
- R
tags:
- R code
---

based on [Google's R Style
Guide](http://google-styleguide.googlecode.com/svn/trunk/google-r-style.html)

see also: [bioconductor's coding
standards](http://wiki.fhcrc.org/bioc/Coding_Standards)

# Filenames
- R code: `*.R`
- man pages: `*.Rd`
- R Data files: `*.RData`
- S4-methods: `*-methods.R`
- non-S4 functions: `*-functions.R`

# Variable/Function/Class names
[camelCase](http://en.wikipedia.org/wiki/CamelCase)
- Variables and functions should start with a lower letter.
- Class should start with a capital one.

```R
fooBar <- 1:10
helloWorld <- function() # ...
setClass("SampleClass", #...
```

# Line Length
max. 80 characters

# Indentation
two spaces, no tabs

# Spacing
- Spaces around all binary operators (`=`, `+`, `-`, `<-`, etc.)
- Space after a comma not before
- Space before left parenthesis not after
- No spaces around `=` when passing arguments in a function call
- No spaces around `:` 

```R
a <- 1:10
b <- a + 1:10

print(x=10)

if (debug) {
  message("Hello World!")
}

```

# Curly Braces
- Opening curly brace in the same line like the statement before.
- Closing curly brace on its own line.
- Always add `{` and `}` after `if`. Do not use the one-line shortcut.

```R
if (debug) {
  message("Hello World!")
}

foobar <- function(x) {
  # ...
}
```

# Assignment

` <- `
