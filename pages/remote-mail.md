<!--
title: Remote Mail
author: Charadon
description: How to connect to your tilde.institute e-mail address remotely.
-->

# Remote Mail Guide
tilde.institute doesn't support POP or IMAP at the moment, so we'll need to use
a little bit of a roundabout way of connecting to our mail address remotely.
All you will need for this guide is sshfs, ssh itself, and an e-mail client
that supports Maildir.

## Known clients that support Maildir
- Gnome Evolution
- Neomutt
- Mutt

## Sending Mail

To send mail, all you need to do is run this command:

```
ssh -nNTL 25:localhost:25 yourusername@tilde.institute
```

And then set your SMTP server in your mail client to localhost and use port 25.
You will now be able to send mail.

## Receiving Mail
First, you need to mount your remote Maildir folder using sshfs. You can use
this command to do that:

```
sshfs -v -o reconnect -o ssh_command="ssh -i ~/.ssh/id_yourkey" yourusername@tilde.institute:/home/yourusername/Maildir ~/Maildir
```

Then set up your mail client like you would with any other Maildir and point it
to your mounted Maildir folder.

### Notes
1. This is not very mobile unfortunately, and as far as i'm aware, there is no
Maildir supporting e-mail client for phones.
2. The above commands assume you have a keyring installed to automatically
unlock your keys OR a passwordless key.
3. On some file managers such as Thunar, if sshfs can't connect to the remote
server, it will freeze the file manager if you navigate to the folder it's
mounted in. (In this case, since we mounted Maildir to ~/, it'll freeze in
your home folder.)
