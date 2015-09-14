---
layout: post
title: R Code Style Guide
categories:
- R
tags:
- code style
---

based on [Google's R Style
Guide](http://google-styleguide.googlecode.com/svn/trunk/google-r-style.html)

see also: [bioconductor's coding
standards](http://www.bioconductor.org/developers/how-to/coding-style/)

# Filenames
- R code: `*.R`
- man pages: `*.Rd`
- R Data files: `*.RData`
- S4-methods: `*-methods.R`
- non-S4 functions: `*-functions.R`

# Variable/Function/Class names
[camelCase](http://en.wikipedia.org/wiki/CamelCase)

- Variables and function names should start with a lower letter.
- Class names should start with a capital one.

{% highlight r %}
fooBar <- 1:10
helloWorld <- function() # ...
setClass("SampleClass", #...
{% endhighlight %}

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

{% highlight r %}
a <- 1:10
b <- a + 1:10

print(x=10)

if (debug) {
  message("Hello World!")
}

{% endhighlight %}

# Curly Braces
- Opening curly brace in the same line like the statement before.
- Closing curly brace on its own line.
- Always add `{` and `}` after `if`. Do not use the one-line shortcut.

{% highlight r %}
if (debug) {
  message("Hello World!")
}

foobar <- function(x) {
  # ...
}
{% endhighlight %}

# Assignment

` <- `

# Comments
Use `## ` (roxygen: `#' `) to start comments.

# Semicolon
Don't use it.

# apply calls
{% highlight r %}
foo <- apply(bar, 2, median)

foo <- sapply(bar, function(x) {
  return(x+1)
})
{% endhighlight %}


