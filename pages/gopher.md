<!--
title: Getting Started With Gopher
description: Using burrow to manage your gopher presence
author: tomasino
-->

# Getting Started With Gopher

# Using `burrow`

To create a gopher hole on tilde.institute, a user can easily get started
by doing the following:

### Create the gopher directory 
``` 
$ mkdir public_gopher 
``` 
### Create a root gophermap 
``` 
$ burrow gophermap 
``` 
Gophernicus will interpret any text you add here as information lines unless they begin with one
of gophernicus' special characters or contains a tab. As a general rule,
don't use tabs unless you're intentionally linking something.

Add a cool header to the file (check out `figlet`!), then somewhere
near the top, paste: 
``` 
==== Last Updated: February 19th, 2019 ====
``` 
The date doesn't matter, really. Whenever you "phlog" with `burrow`
it will update the date for you. How sweet is that?

Now lets add a link to your phlog that you're totally going to have:

``` 
1phlog[tab]phlog 
```

That `[tab]` should be a literal tab, though. Make sure your editor
doesn't convert it to spaces. Now, save and quit the editor.

### Create a phlog directory 
``` 
$ mkdir ~/public_gopher/phlog 
``` 
### Now create a new phlog with burrow 
``` 
$ burrow phlog 
```

You'll be prompted for a title. If you hit enter and give no title then
burrow will abort.

Once you hit enter after giving your title a temporary file will open in
your default `$EDITOR`. Don't like that editor? Be sure to change your
environment var!

If you quit your phlog file without saving the post is aborted. If you save
and quit, it will create a new phlog entry, add it to your phlog gophermap
that now exists, and update the date on your root gophermap. That's it!

You have an RSS file sitting in the root of your gopher hole at
`rss.xml`. It will automatically generate when you phlog, like a
winner. You can edit your root `gophermap` at any time by using burrow's
`gophermap` action. If you create other folders and gophermaps in the
future you can use burrow's gophermap function to target them. For
instance, to open the phlog listings you would: 
``` 
$ burrow gophermap /phlog 
``` 
Editing gophermaps with `burrow` will ensure they're always
saved and formatted properly! Any other files are just text, so open them
directly with your editor of choice.

That's it! Happy gophering.

~tomasino

[back](/)

