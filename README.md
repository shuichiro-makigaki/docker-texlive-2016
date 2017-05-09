[![Docker Automated build](https://img.shields.io/docker/automated/makisyu/texlive-2016.svg)](https://hub.docker.com/r/makisyu/texlive-2016/) [![Docker Build Status](https://img.shields.io/docker/build/makisyu/texlive-2016.svg)](https://hub.docker.com/r/makisyu/texlive-2016/)

*TeX Live 2016 has been frozen since May 16th 2017* for TeX Live 2017 release preparation. No more updates for it forever.
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

# Image is too large.
Ooops. I know!
