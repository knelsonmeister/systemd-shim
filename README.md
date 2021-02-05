# systemd-shim for MX Linux
This repo contains a fork of systemd-shim.  It builds a Debian Buster/Bullseye based debian package for MX Linux.
It depends on a modified systemd (available here: https://github.com/knelsonmeister/systemd)

## Background:
Systemd-shim allows a system to boot up using a SYSV init, but still be able to support the modern programs that depend on systemd.  It is not perfect, but it allows for a Linux distribution to support both SYSV init and systemd as a choice in the grub boot menu.  MX Linux does just that.
Debian used to support systemd-shim, but support was dropped in Debian Buster.  This repo and the systemd repo linked above are an effort to maintain the systemd-shim support in Debian Buster and Debian Bullseye.

## Current Version: 10-4
Based on:
- https://github.com/desrt/systemd-shim
- http://deb.debian.org/debian/pool/main/s/systemd-shim/systemd-shim_10-3.debian.tar.xz

## Changes:
  - Added new patch: buster-support
      - Patch adds supports for querying LoadState needed to reboot/shutdown
  - Updated debian/patches/series file to add new patch
  - Updated debian/changelog to increment version to 10-4

## How To Build:
```
git clone https://github.com/knelsonmeister/systemd-shim.git
cd systemd-shim
ln -s debian/patches .
quilt push -a
dpkg-buildpackage -uc -us -b
cd ..
```
