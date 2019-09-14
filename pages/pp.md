<!--
title: pp(1)
description: Introduction to pp(1)
author: ahriman / gbmor
-->

# pp(1)

`pp(1)` is a shell preprocessor developed by our own user [adi](https://adi.tilde.institute).
It allows one to embed shell into any text file between instances of the token `#!`. This powerful
tool allows the dynamic generation of static pages using standard bourne shell.

For example:
```
<!doctype html>
<title>pp(1) example</title>
<ul>
#!
i=1
while test $i -le 10
do
if test $((i % 2)) -eq 0
then
#!
	<li class=even>$i</li>
#!
else
#!
	<li class=odd>$i</li>
#!
fi
i=$((i + 1))
done
#!
</ul>
```
Will output, per the manual page:
```
<!doctype html>
<title>pp(1) example</title>
<ul>
        <li class=odd>1</li>
        <li class=even>2</li>
        <li class=odd>3</li>
        <li class=even>4</li>
        <li class=odd>5</li>
        <li class=even>6</li>
        <li class=odd>7</li>
        <li class=even>8</li>
        <li class=odd>9</li>
        <li class=even>10</li>
</ul>
```

The manpage includes more information on advanced features, such as piping `stdin` and debugging.

## Notes
* Full Guide: [adi.tilde.institute/pp](https://adi.tilde.institute/pp)

[back](/)
