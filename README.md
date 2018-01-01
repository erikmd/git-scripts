# git-scripts

This repo is intented to gather some handy scripts that extend the
standard behavior of Git.

It currently contains:

## [git-format-patch-follow](bin/git-format-patch-follow)

```
Facility to export the Git history of given files, including renames.

Usage:
  git format-patch-follow [<options>...] [--follow] [--] [<paths>...]

Example:
  git format-patch-follow --stdout --root --follow -- file1... > patch

Summary:
  This command accepts the very same arguments as 'git format-patch',
  as well as the '--follow' option.

  If this option '--follow' is passed to 'git format-patch-follow', all
  subsequent arguments that are not options themselves are considered
  as relative file names to be pre-processed by 'git log --follow' to
  retrieve the absolute paths of these files, including renames, which
  are then processed by vanilla 'git format-patch'.

Credits:
  git-format-patch-follow was written by Erik Martin-Dorel and it is
  distributed under the MIT license <//opensource.org/licenses/MIT>.
```

## Installation

To be able to use `git format-patch-follow` in a (Bash) terminal, you
just need to download the script
[git-format-patch-follow](https://github.com/erikmd/git-scripts/raw/master/bin/git-format-patch-follow),
set its execute permission, and put it in your `PATH`.
