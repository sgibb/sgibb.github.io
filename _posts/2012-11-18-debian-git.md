---
layout: post
title: Debian Packaging - Cheat Sheet
categories:
- debian
tags:
- debian
---

# README
* [deb new maintainer's guide](http://www.debian.org/doc/manuals/maint-guide/)
* [deb policy manual](http://www.debian.org/doc/debian-policy/)
* [git workflow](http://www.eyrie.org/~eagle/notes/debian/git.html)
* [machine readable copyright file](http://dep.debian.net/deps/dep5/)

# Setup system

    apt-get install git-buildpackage cowbuilder
    sudo cowbuilder --create

# Setup package environment

    mkdir PROJECT && cd PROJECT
    mkdir development build-area tarballs

    # download upstream tarball to tarballs

    cd development
    git init
    git commit --allow-empty -m "initial commit"
    git branch upstream
    git-import-orig ../tarballs/PROJECT.tar.gz
    mkdir debian

    # package

# Work on a package

    sudo cowbuilder --update
    # ...
    git add debian/*
    git commit -m "..."
    git-buildpackage
