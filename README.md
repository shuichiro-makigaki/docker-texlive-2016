[![Docker Automated build](https://img.shields.io/docker/automated/makisyu/texlive-2016.svg)](https://hub.docker.com/r/makisyu/texlive-2016/) [![Docker Build Status](https://img.shields.io/docker/build/makisyu/texlive-2016.svg)](https://hub.docker.com/r/makisyu/texlive-2016/)

**TeX Live 2016 has been frozen since May 16th 2017** for TeX Live 2017 release preparation. *No more updates for it forever.*

Please note that this is good news. Thank you and good bye, TeX Live 2016!

# Dockerfile for TeX Live 2016

This is a Dockerfile repository of TeX Live 2016 with scheme-full profile. (Almost) monthly updated.

# Usage

A path to TeX Live scripts and binaries (`/usr/local/texlive/2016/bin/x86_64-linux`) is already added to `$PATH`.

``` shell
$ docker run --rm -i -t makisyu/texlive-2016 platex
This is e-pTeX, Version 3.14159265-p3.7-160201-2.6 (utf8.euc) (TeX Live 2016) (preloaded format=platex)
 restricted \write18 enabled.
**
! End of file on the terminal... why?
```

Most users want to add a volume that contains source codes and change working directory to it.

``` shell
$ ls
main.tex
$ docker run --rm --volume $PWD:/workdir --workdir /workdir makisyu/texlive-2016 platex main.tex
```

Docker volume is mounted as `uid=1000,gid=1000` (In most cases, these ids mean `root:root`.), and files in the directories are owned by root. Adding `--user` option is good idea.

You should use uid/gid instead of user/group names because, in the container, `/etc/passwd` doesn't contain your user/group names. If you use `uid:gid`, the container creates files as specified `uid:gid` without reading `/etc/passwd`.

``` shell
$ docker run --rm --volume $PWD:/workdir --workdir /workdir --user 1001:1001 makisyu/texlive-2016 platex main.tex
```

`latexmk`? Yes, it's very useful, and scheme-full profile includes huge collection of other useful tools.

``` shell
$ ls -a
.latexmkrc main.tex
$ docker run --rm --volume $PWD:/workdir --workdir /workdir --user 1001:1001 makisyu/texlive-2016 latexmk
```

This image is based on fedora:latest. Shell and other basic utilities are available, and you can run shell script, perl, etc.

``` shell
$ docker run -i -t --rm --volume $PWD:/workdir --workdir /workdir --user 1001:1001 makisyu/texlive-2016 /usr/bin/bash
[root@20629bec6417 workdir]# ls
main.tex
[root@20629bec6417 workdir]# perl -v

This is perl 5, version 24, subversion 1 (v5.24.1) built for x86_64-linux-thread-multi
(with 68 registered patches, see perl -V for more detail)

Copyright 1987-2017, Larry Wall

Perl may be copied only under the terms of either the Artistic License or the
GNU General Public License, which may be found in the Perl 5 source kit.

Complete documentation for Perl, including FAQ lists, should be found on
this system using "man perl" or "perldoc perl".  If you have access to the
Internet, point your browser at http://www.perl.org/, the Perl Home Page.

[root@20629bec6417 workdir]# python3.5 -V
Python 3.5.3
[root@20629bec6417 workdir]#
```

# Image is too large.
Ooops. I know!
