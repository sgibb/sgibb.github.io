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
* [debian/watch](http://wiki.debian.org/debian/watch/)

# git repositories

* [debian-med](http://anonscm.debian.org/gitweb/?pf=debian-med)
* [debichem](http://anonscm.debian.org/gitweb/?pf=debichem)

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

# Import new version

    cd PROJECT/development/
    ./debian/rules get-orig-source
    git-import-orig ../tarballs/PROJECT_NEW_VERSION.tar.gz
    sudo cowbuilder --update
    git-buildpackage

