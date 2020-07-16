<!--
title: todo, a todo list manager
description: todo usage guide
author: ensa
-->

# todo, a todo list manager

`todo` is a todo list manager.

`todo` manages the todo list stored in the path referred to by `$TODO`, or
`$HOME/todo` if TODO isn't set.

## basic usage

`todo` without arguments will print the file's
contents, with line numbers added.
example output:
```
     1  write todo documentation
     2  water the cat
     3  do nothing
```

`todo -a "MSG"`
will append another line, containing MSG.
```
     1  write todo documentation
     2  water the cat
     3  do nothing
     4  MSG
```

`todo -e` edits the todo file in `$EDITOR`.

`todo -d 2` removes item 2 from the list, and archives it in `${TODO}.complete`
with a timestamp.
`todo` output after `todo -d 2`:
```
     1  write todo documentation
     2  do nothing
     3  MSG
```

`todo -x` views the list archive.
example output:
```
2020-07-16 13:37:53 - water the cat
```

## advanced use

the `-n` flag specifies the line number where the line is added, pushing all
lower lines down by one.
for example, `todo` after `todo -n 3 -a 'bake pie'` will result in this.
```
     1  write todo documentation
     2  do nothing
     3  bake pie
     4  MSG
```

## source repository
todo's source can be found [here](https://git.tilde.institute/ensa/todo).

[back](/)
