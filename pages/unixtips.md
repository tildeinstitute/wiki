<!--
title: UNIX ProTips
description: Handy tips for budding power users
author: xvetrd
-->

# UNIX ProTips

I realized today I wasn't getting mail notifications, and I hadn't set
them up on this shell. So here are some things I do on my local machine
that work here:

To get the shell to tell you when you have new mail, after command
executions, add this to your `.profile` or your `.kshrc` files 
(or other shell RC file) in your home directory.

```
export MAILCHECK=0
```

And, if you want, you can have a persistent notification when
you have un-incorporated mail, or more specifically, when your
`/var/mail/<username>` isn't empty.

```
PS1="\$([-s /var/mail/`whoami` ] && echo '* ')$PS1"
```

This works in `/bin/ksh`, I can't speak for other shells.

If anybody else has some quick tips they would like to share, I encourage
them to edit this page.

Happy Unixing!

[back](/)
