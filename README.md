# wiki.tilde.institute

This repository holds the wiki data for tilde.institute

To contribute:
* Fork the repository
* Create a branch with an appropriate name:
  * `git checkout -b mycoolpage`
* Add your page in the `pages/` directory
* Submit a PR
* Once it's merged it will be pulled into the wiki

Don't forget to wrap lines at approximately 75 columns. If
you need to, use `fmt -w 75`. For example:

```
$ fmt -w 75 mypage.md | tee mypage.md
```
Then afterwards, check the page to fix anything that got
clobbered.

## Software

The wiki engine being used is [TildeWiki](https://github.com/gbmor/tildewiki), developed by ahriman
