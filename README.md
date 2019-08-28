# systemd-shim for MX Linux
This repo contains a fork of systemd-shim.  It builds a Debian Buster based debian package for MX Linux.
It depends on a modified systemd (available here: https://github.com/knelsonmeister/systemd)

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
