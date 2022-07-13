<!--
title: gcc and GNUstep
description: Information on using recent gcc versions
author: gbmor
-->

# gcc

OpenBSD includes `gcc4` in the base install, which is `gcc-4.2.1`.
If you prefer to use `gcc-11.2.0`, the names of the binaries differ.

The following are part of `gcc-11.2.0`:

* `/usr/local/bin/egcc`
* `/usr/local/bin/gcc` (symlink)
* `/usr/local/bin/eg++`
* `/usr/local/bin/g++` (symlink)
* `/usr/local/bin/egdb`
* `/usr/local/bin/gdb` (symlink)
* `/usr/local/bin/egfortran`
* `/usr/local/bin/gfortran` (symlink)
* `/usr/local/bin/gnat`

The following are part of `gcc-4.2.1`

* `/usr/bin/gcc4`
* `/usr/bin/g++4`
* `/usr/bin/gdb`

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

