<!--
title: gcc-8
description: Information on using gcc-8
author: gbmor
-->

# gcc-8

OpenBSD includes `gcc` in the base install. However, it includes `gcc-4.2.1`.
If you prefer to use `gcc-8.3.0`, the names of the binaries differ so as to not
conflict with `gcc` in base.

* `egcc` - gcc
* `eg++` - g++
* `egdb` - gdb
* `egfortran` - g95 / gfortran

The exception being `gnat`.

`GNUstep` is available if you would like to develop using Objective-C. The
following should be added to `~/.kshrc`:

```
export GNUSTEP_MAKEFILES=/usr/local/share/GNUstep/Makefiles
. /usr/local/share/GNUstep/Makefiles/GNUstep.sh
```
You will also need to call `gmake` rather than `make` when building Objective-C
code. See [this StackOverflow post](https://stackoverflow.com/questions/14441852/how-to-build-gnustep-programs-on-openbsd)
for more information.

[back](/)
