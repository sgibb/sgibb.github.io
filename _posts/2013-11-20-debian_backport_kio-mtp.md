---
layout: post
title: Backport kio-mtp to Debian GNU/Linux 7.0 wheezy
categories:
- debian
tags:
- debian
- backports
---

based on [https://wiki.debian.org/SimpleBackportCreation](https://wiki.debian.org/SimpleBackportCreation)

# Install development tools

{% highlight bash %}
su -c "apt-get install devscripts build-essential debian-keyring fakeroot"
{% endhighlight %}

# Download the .dsc file from sid

Visit
[http://packages.debian.org/sid/kio-mtp](http://packages.debian.org/sid/kio-mtp)
and look for the `.dsc` file.

Download and extract debian source package:

{% highlight bash %}
dget -x http://ftp.de.debian.org/debian/pool/main/k/kio-mtp/kio-mtp_0.75+git20130806-2.dsc

cd kio-mtp-0.75+git20130806
{% endhighlight %}

# Install dependencies

{% highlight bash %}
grep -1 Build-Depends debian/control
# Uploaders: Felix Geyer <fgeyer@debian.org>
# Build-Depends: debhelper (>= 9), pkg-kde-tools, cmake, kdelibs5-dev,
# libmtp-dev, pkg-config

su -c "apt-get install debhelper pkg-kde-tools cmake kdelibs5-dev libmtp-dev pkg-config"
{% endhighlight %}

# Update debian/changelog

{% highlight bash %}
dch --local ~bpo70+ --distribution wheezy-backports "Rebuild for wheezy-backports."
{% endhighlight %}

# Build package (without GPG signing)

{% highlight bash %}
dpkg-buildpackage -us -uc
{% endhighlight %}

# Install it

{% highlight bash %}
su -c "dpkg -i ../kio-mtp_0.75+git20130806-2~bpo70+1_amd64.deb"
{% endhighlight %}

