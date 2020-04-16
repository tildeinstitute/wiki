<!--
title: GnuPG for SSH Authentication
Description: Using gpg-agent as an alternative to ssh-agent
author: gbmor
-->

# Using GPG for SSH Authentication

It's a fairly simply process to have gpg-agent handle your SSH
authentication. To start off, you'll need to have a private GnuPG key
generated with an appropriate subkey for authentication. Once that's
taken care of, open up `~/.gnupg/gpg-agent.conf`

```
$ cat ~/.gnupg/gpg-agent.conf
    enable-ssh-support
    default-cache-ttl 60
    max-cache-ttl 120
```

Now you'll need to append the following to `~/.bashrc`, or the appropriate
rc file for your shell

```
$ cat ~/.bashrc
    export GPG_TTY="$(tty)"
    export SSH_AUTH_SOCK=$(gpgconf --list-dirs agent-ssh-socket)
    gpg-connect-agent updatestartuptty /bye > /dev/null
```

Once that's done, you'll need to let `gpg-agent` know which GnuPG subkey
to use for SSH authentication. Run the following and copy the keygrip
associated with the subkey you've generated specifically for authentication.
Don't use *my* keygrip, however. The output here is just for an example. `GnuPG`
computes the keygrips from the public key, so nothing here is sensitive
or private.

```
$ gpg --with-keygrip -k ben@gbmor.dev
    pub   rsa4096/0xEAB272409CD12FF0 2018-11-25 [SC]
        Key fingerprint = 291A AFF7 A291 7DAB 0E01  6B9C EAB2 7240 9CD1 2FF0
        Keygrip = DE06FAA273017BBD8778F94639611CEF53AB9EBC
    uid                   [ultimate] Ben Morrison <ben@gbmor.dev>
    sub   rsa4096/0xF9C3B650612249D9 2018-11-25 [E]
        Keygrip = 751ADAC109736316B6ABEBB3F2BDF4612F8A630C
    sub   rsa4096/0x4969E5731CFEB507 2018-11-25 [A]
        Keygrip = 44D1BDC0C1931E2E018E7CE49CDE14BFB4EA11E3
    sub   rsa4096/0x8F192E4720BB0DAC 2018-11-25 [S]
        Keygrip = 240966CBF2791D8C34D0DA646925435FED49F9BF
```

Now, open `~/.gnupg/sshcontrol` and paste the keygrip into that file.
It's the keygrip just below the key marked `[A]` for authentication.
Verify that the correct keygrip has been selected by running these two
and comparing the output:
```
$ ssh-add -L
    ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCakJKfXUuX/ZDxJQySdxCeQfxTu0g
    KPCESGDyadvFAPDxtcTfOrxfqJLZx8CodkC7hzHT/QEy/xMgN18Q== cardno:000609861127
```
```
$ gpg --export-ssh-key <keyid>
    ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCakJKfXUuX/ZDxJQySdxCeQfxTu0g
    KPCESGDyadvFAPDxtcTfOrxfqJLZx8CodkC7hzHT/QEy/xMgN18Q== openpgp:0x1CFEB507
```
The `ssh` output should match the `gpg` output (except maybe the little 
trailing comment, like here). Also, I've removed most of the public key I'm using as
an example for brevity's sake. It should be quite a bit longer than this.
If `ssh` is correct, kill off `gpg-agent`
```
$ pkill gpg-agent
```

Then open up a new terminal and attempt to connect to a server!

[back](/)
