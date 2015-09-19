---
layout: post
title: Configuring University Cambridge VPN on Debian Jessie
categories:
- debian
tags:
- vpn
- cambridge
- jessie
---

You could find an instruction how to configure the University Cambridge VPN on
Ubuntu at
[Configuring the UIS VPN on Ubuntu Desktop 14.04 LTS](http://www.ucs.cam.ac.uk/vpn/ubuntu14).

While it is possible to configure the strongswan VPN the connection fails with
the following error:

    The VPN service 'org.freedesktop.NetworkManager.strongswan' was not installed.

Unfortunately the package *network-manager-strongswan* is not available for
*Debian Jessie*.

Nevertheless it is not too hard to build this package for jessie and to
configure the VPN.

# Backporting network-manager-strongswan

This howto is based on [SimpleBackportCreation](https://wiki.debian.org/SimpleBackportCreation).

First you have to install the debian packaging tools:

```bash
su -c "apt-get install packaging-dev debian-keyring devscripts equivs"
```

Afterwards you have to download the *.dsc* file:

```bash
dget -x http://http.debian.net/debian/pool/main/n/network-manager-strongswan/network-manager-strongswan_1.3.1-1.dsc
```

Install missing dependencies:

```bash
cd network-manager-strongswan-1.3.1/
su -c "mk-build-deps --install --remove"
```

Add a backport revision number:

```bash
dch --local ~bpo80+ --distribution jessie-backports "Rebuild for jessie-backports."
```

Build the package without GPG signing

```bash
dpkg-buildpackage -us -uc
```

# Install the necessary packages

```bash
su
dpkg -i ../network-manager-strongswan_1.3.1-1~bpo80+1_amd64.deb
## fix missing dependencies
apt-get install -f
## install eap-mschapv2 plugin
apt-get install libcharon-extra-plugins
## restart network-manager
systemctl restart network-manager.service
```

# Configure your VPN connection

Select *Add network* > *StrongSwan* in the network configuration dialog and use
the following settings:

- Gateway: *vpn.uis.cam.ac.uk*
- Certificate: *none*
- Authentication: *EAP*
- Username: *CRSid@cam.ac.uk*
- Password: *Network Access Token*
- Request an inner IP address: *Check*
- Enforce UDP encapsulation: *Check*
