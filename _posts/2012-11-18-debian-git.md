---
layout: post
title: Debian Packaging - Cheat Sheet
categories:
- debian
tags:
- debian
---

# README
* [deb new maintainer's guide](https://www.debian.org/doc/manuals/maint-guide/)
* [deb policy manual](https://www.debian.org/doc/debian-policy/)
* [git workflow](http://www.eyrie.org/~eagle/notes/debian/git.html)
* [machine readable copyright file](http://dep.debian.net/deps/dep5/)
* [debian/watch](http://wiki.debian.org/debian/watch/)

# git repositories

* [debian-med](https://salsa.debian.org/med-team)
* [debichem](https://salsa.debian.org/debichem-team)

# qa pages

* [debichem](http://qa.debian.org/developer.php?login=debichem-devel@lists.alioth.debian.org)
* [sgibb](http://qa.debian.org/developer.php?login=sgibb.debian@gmail.com)

# dashboard

* [sgibb/debichem](http://udd.debian.org/dmd.cgi?email1=sgibb.debian%40gmail.com&email2=debichem-devel%40lists.alioth.debian.org&email3=&packages=&ignpackages=)

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

