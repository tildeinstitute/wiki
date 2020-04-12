<!--
title: firefox address bar tips
author: erxeto
description: Some useful tips for using the firefox address bar more
efficiently
-->

# Firefox address bar.

The address bar has become our entry point to the internet these days.
Firefox in its default configuration does some sort of _smart_ guess on
what you type there.  If it resembles a [URL][https://en.wikipedia.org/wiki/URL]
then the browser makes that request.  If not, it sends the string you typed
to your default search engine.  It also includes some fuzzy search matches
from your history and all that, which is fine 90% of the time, but
sometimes you need a bit more control over what results it shows you.

# Changing the address bar behaviour

This is a list of modifiers you can set at the beginning of the search to
tell firefox what do you want to see on the results, a kind of filtering:

```
^    to search for matches in your browsing history.
*    to search for matches in your bookmarks.
+    to search for matches in pages you've tagged.
%    to search for matches in your currently open tabs.
#    to search for matches in page titles.
$    to search for matches in web addresses (URLs).
?    to search for matches in suggestions.
```

# Examples

So, if you want to search for the word `headphones` in your bookmarks only,
you can type on the address bar:

`*headphones`

And, if you want to include only the results of your browsing history it
would be:

`^headphones`

[back](/)
