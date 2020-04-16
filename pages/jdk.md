<!--
title: jdk 11
description: Using JDK 11
author: gbmor
-->

# jdk 11

To use JDK 11 for development, you will need to make the following additions
to your `~/.kshrc` file:

```
export PATH=/usr/local/jdk-11/bin:$PATH
export JAVA_HOME=/usr/local/jdk-11
```

Afterwards, you may call `java`, `javac`, etc as expected.

JDK 1.8.0 is also available by replacing `jdk-11` in the above two lines
with `jdk-1.8.0`

[back](/)
