<!--
title: NNTP
description: Newsgroup service information
author: gbmor
-->

# NNTP

Our friends over at [tilde.club](https://tilde.club) run an NNTP service that's
open to the public. There are a few options for browsing from [tilde.institute](https://tilde.institute).

```
news.tilde.club:119
```

## lynx

If you just want to take a look, `lynx` can connect to an `NNTP` service:

```
lynx news://news.tilde.club
```

## tin

`/etc/nntpserver` has been populated with `news.tilde.club`, so connecting with tin
only requires this command:

```
tin -r
```

`-r` for remote newsgroups. Once connected, hit `s` to subscribe, then `*` to subscribe
to all newsgroups. To start a new thread, pick a group, then hit `w` for "write" and
compose your message. To respond to a message in a thread, hit `f` for "follow-up". There
are a few other options for interaction with a post or thread, such as `r` for a direct
email reply to the post author.

## alpine

Start `alpine`, then navigate to `Setup`, and finally `Config`. Set the following options:

* NNTP Server: `news.tilde.club`
* SMTP Server: `localhost:25`

## Other Clients

If you have another preferred client, feel free to ask us to install it. Either mail
`admins@tilde.institute` or jump into the IRC channel `#institute`.

## See Also

[https://tilde.club/wiki/usenet-news.html](https://tilde.club/wiki/usenet-news.html)


[back](/)
