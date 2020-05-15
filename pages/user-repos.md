<!--
title: User git Repositories
description: Getting set up with git.tilde.institute
author: gbmor
-->

# User git Repositories

There's now an instance of [cgit](https://git.zx2c4.com/cgit) available for all users to enjoy. Unlike the previous git repo hosting platform I used, this does not require an additional signup. It's available directly from your home directory. Tagged versions are automatically bundled into `.tar.gz` archives and listed on the summary page.

All repos can be viewed at [https://git.tilde.institute](https://git.tilde.institute)

## Creating the directory

New users will not have to do this step. A `~/public_repos` file will exist in your home directory. If you were a user before this was set up (2020 May 1), you will need to create a symlink in your home directory pointing into location in the httpd chroot where cgit will scan for your repos.

There should be a directory corresponding to your username at the following location:

```
/var/www/cgit_repos/<USER>
```

Issue this command to create the symlink:

```
ln -s /var/www/cgit_repos/$USER ~/public_repos
```

## Adding a repository

Once `~/public_repos` exists, `cd` into it and create a directory for your repo:

```
mkdir foo.git
```

Change into *that* directory and initialize a bare repo:

```
cd foo.git; git init --bare
```

Now that the bare repo has been created, edit the file called `config` and append the following section:

```
[gitweb]
    owner = user_name <user_name@tilde.institute>
    description = My awesome repo!
```

If you prefer, you can skip the `description` field above and just write out the text description of your repo into a file called `description`:

```
echo "My awesome repo!" > description
```

If both exist, the field in `config` will be favored by cgit.

## Setting up the remote

Navigate to your repository on your home computer, and add the following remote, replacing `<USER>` with your username at tilde.institute, and `<REPO>` with the repo name:

```
git remote add tilde.institute <USER>@tilde.institute:public_repos/<REPO>
```

Now it's time to push to the repo you set up on tilde.institute:

```
git push -u tilde.institute master
```

## Checking the repo on [git.tilde.institute](git.tilde.institute)

Your repo should now be available at `https://git.tilde.institute/<USER>/<REPO>`, without the `.git` extension on the repo's directory.

If something's wrong, double-check everything, and then jump into `#institute` on IRC.

## What about pull requests?

These don't exist. I suggest directing people to use [git send-email](https://git-send-email.io) for patches.

## Namespacing projects

cgit will use the directory structure to namespace projects, if you want to group related repositories.

For example, say you have a project called `widget`, which comprises the two repos `libwidget` and `widget-cli`. One way to present this here would be to use the following directory structure in `~/public_repos`

```
~/public_repos/widget
~/public_repos/widget/libwidget.git
~/public_repos/widget/widget-cli.git
```

This will then show up in cgit as:

```
$USER
  widget/libwidget
  widget/widget-cli
```

When setting up the remote in your local copy of the repo, you would use this for the `libwidget` example:

```
git remote add tilde.institute <USER>@tilde.institute:public_repos/widget/libwidget
```

## Misc

You can link to just your own repos via `https://git.tilde.institute/<USER>`

The following files will be parsed into an `about` page for a given repo, in order:

* `README`
* `README.7`
* `README.1`
* `README.txt`
* `README.md`

[back](/)

