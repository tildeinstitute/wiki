<!--
title: IRC
description: Introduction to our IRC network
author: gbmor
-->

# IRC

To connect to the [tildeverse IRC network](https://tilde.chat) and begin
chatting while logged on to tilde.institute, simply use the command
`chat`! If you prefer to use a different IRC client than the default,
such as `irssi`, the following server information will apply:

* localhost
* Port 6667
* No TLS

Don't forget to `/join #institute` and `/join #meta`.

**NOTE:** You must register with `nickserv` to talk in `#meta`:
```
/msg nickserv register <password> <email>
```

## Certificates

If you get an untrusted certificate error, change the weechat configs:
```
/set weechat.network.gnutls_ca_file "/etc/ssl/cert.pem"
```

## Channels

There are quite a few channels on tilde.chat, however some have more
activity than others. Here's a few channels that you may be interested in.

* `#meta` - the general chat channel for all of the [tildeverse](https://tildeverse.org)
* `#helpdesk` - the place to ask IRC operators questions
* `#institute`- for tilde.institute-related discussion
* `#tilderadio` - the channel for the [tildeverse radio station](https://tilderadio.org)
* `#cosmic` - discussions pertaining to [cosmic voyage](https://cosmic.voyage), a
`tilde` focusing on collaborative science fiction writing
* `#tildetel` - the channel for [tilde.tel](https://tilde.tel), the neighborhood SIP server
* `#security` - computer, software, and network security discussions
* `#hamradio` - the channel for hams!
* `#gopher` - for the gopher protocol
* `#gemini` - discussion for the Gemini protocol

You can check the currently available channels any time by issuing `/list`
in your IRC client.

## Connecting Externally

Want to hang out on the tildeverse when you aren't connected to
tilde.institute? No problem! Just use these settings in your favorite
IRC client:

* irc.tilde.chat
* Port 6697
* TLS/SSL is required

The DNS round robin will connect you to one of the nodes in the network.

If you're using `weechat` the following will connect you:

```
/server add tilde irc.tilde.chat/6697 -ssl -autoconnect
/connect tilde
```

And if you're using `irssi`

```
/connect -tls -tls_verify irc.tilde.chat 6697
```

Or from `catgirl`:

```
catgirl -h institute.tilde.chat -n <nick>
```

The tildeverse IRC network also runs an instance of `The Lounge`, a
web-based IRC client that allows you to stay connected even when you're
away. It's available at:

* [https://web.tilde.chat](https://web.tilde.chat)

Join us on the tildeverse IRC network and socialize with other tilde users!

[back](/)
