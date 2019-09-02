<!--
title: pass, the CLI Password Manager
author: erxeto
description: Usage guide for pass
-->

# pass, the CLI Password Manager

`pass` is a command line utility to manage your passwords.

It creates a simple file/folder structure under your `$PASSWORD_STORE_DIR`
(by default `~/.password-store`) where every file is encrypted with your
gpg key.

You can organize that hierarchy as you see fit. For instance something like
`sites/tilde.news/myusername` is a common way of doing it.

Those files are not limited to contain simply a password, they can contain
anything. But is recommended that the password goes alone in the first
line, so you can benefit from the `-c` option which copies that to the
clipboard directly.

There is `bash`, `zsh` and `fish` command line completion available and
all can be tracked using `git`. So it's really convenient.

## Setup

This is simple, just one command (assuming you have your GnuPG key
ready). GPG-ID is the hex id of your key.

```
$ pass init GPG-ID
    mkdir: created directory ‘/home/user/.password-store’
    Password store initialized for GPG-ID
```

## Basic Usage

List all passwords "tree" style

```
$ pass Password Store
├── sites
│   ├── tilde.zone
│   │   ├── myUserName
│   │   ├── secondAccount ...
```

Find a password

```
$ pass find tilde.zone
Search Terms: tilde.zone
└── sites
    └── tilde.zone
        └── myUserName@tilde.zone
```

See the content of a file

```
$ pass email/tilde.institute/myAccount
    supersecret
```

Copy the first line to the clipboard. Clear time can be configured with
`$PASSWORD_STORE_CLIP_TIME`

```
$ pass -c email/tilde.institute/myAccount
    Copied email/tilde.institute/myAccount to clipboard.
    Will clear in 45 seconds.
```

Insert a new password. It can be multiline with `-m`. Remember to put the
password on the first line if you want to use the clipboard function 

```
$ pass insert sites/foo.com/blah
    Enter password for sites/foo.com/blah:
```

Generate a 32 chars random password and store it. You can define the
default length with `$PASSWORD_STORE_GENERATED_LENGTH`. With `-n` the
password will not include symbols, but alphanumeric characters only. With
`-c` it gets copied to the clipboard as usual.
```
$ pass generate sites/foo.com/abcd 32
    The generated password to sites/foo.com/abcd is: 
        $(-QF&Q=IN2nFBx)
```

take a look at the `--help` option or the complete documentation on
their website.

## Changing Keys

If you need to change the key being used for your password files,
simply navigate to the directory and re-issue `pass init`, but with
the ID of the new key to be used. Pass will prompt for the old key's
password, then automatically decrypt all keys and re-encrypt them
with the new key.
```
$ cd ~/.password-store
$ pass init NEWGPGKEYID
```

references:

* [pass home page](https://passwordstore.org)

[back](/)
