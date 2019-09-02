<!--
author: ahriman
title: BCHS Guide
description: Introduction to the BCHS stack for web development
date: 2019-04-24
-->

# BCHS Guide

This will be a quick-and-dirty guide to getting started with the BCHS
stack. More information can be found at:

* [Learn BCHS](https://learnbchs.org)
* [pledge(2)](http://man.openbsd.org/cgi-bin/man.cgi/OpenBSD-current/man2/pledge.2)
* [unveil(2)](http://man.openbsd.org/unveil.2)
* [kcgi](https://kristaps.bsd.lv/kcgi/)
* [ksql](https://kristaps.bsd.lv/ksql/)
* [kwebapp](https://kristaps.bsd.lv/kwebapp)

tilde.institute is set up to process all files with the `.cgi` extension
via `slowcgi(8)`. This allows for a multitude of possibilities -
any compiled language can be used to develop web applications on an
OpenBSD server. It's advised to use `C` because of the `pledge(2)` and
`unveil(2)` system calls available, which allow for restricting privileges
and restricted filesystem access, respectively.

Keep in mind that if you don't use the previously listed
`kcgi`/`ksql`/`kwebapp` libraries, you will need to work with HTTP's
eccentricities manually. For an example, [here's the Hello World
code](https://tilde.institute/helloworld.c) from the LearnBCHS
site. And [here it is running](https://tilde.institute/helloworld.cgi)
as compiled CGI here at tilde.institute.

Once you've written your software to be served via CGI, be sure to
statically link the executables. Sure, there's a larger file size, but
the benefits outweigh that in this case - there's no relying on what
I may or may not have installed on tilde.institute. For example:

```
$ cc -static -g -W -Wall -o app.cgi app.c
```

When you've completed compilation, make sure to set permissions properly
(755) and move it to the public folder in your home directory. `httpd(8)`
is set to use `index.html` as the index file, however this can be changed
to `index.cgi` or what-have-you by contacting the admins.

~institute user `xvetrd` has written a more detailed example on
`kcgi` than is provided on the library's site. It includes an
example `makefile` as well. The KCGI Starter archive is [available
here](https://tilde.institute/kcgi-starter.tar.gz). Simply 
```
curl -O https://tilde.institute/kcgi-starter.tar.gz
``` 
it to your home directory here on ~institute, 
```
$ tar xzf kcgi-starter.tar.gz
$ cd kcgi-starter
$ make
$ make install
```
to test the compilation. It installs to `~/public_html` with the proper
ownership and permissions. View the `index.c` source and the `makefile`
to see what goes on under the hood! Feel free to adapt it your own projects!

[back](/)

