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

### Installation

To be able to use `git format-patch-follow` in a (Bash) terminal, you
just need to download the script
[git-format-patch-follow](https://github.com/erikmd/git-scripts/raw/master/bin/git-format-patch-follow),
set its execute permission, and put it in your `PATH`.

## [git-pr](bin/git-pr)

```
Facility to fetch a read-only branch from a GitHub repo Pull Request.

Usage:
  git pr <ID> [<REMOTE>]

Example:
  git pr 390 upstream

Summary:
  BEWARE that the local branch "pr/ID" is always overwritten.
  If the REMOTE argument is omitted, it defaults to "origin".
  REMOTE must point to a GitHub repository.

  This command creates (and overwrites) a local branch named "pr/ID",
  matching the source branch for PR #ID submitted in the REMOTE repo.

See also:
  - https://stackoverflow.com/a/62432946/9164010
  - https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/checking-out-pull-requests-locally
  - https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/allowing-changes-to-a-pull-request-branch-created-from-a-fork

Credits:
  The git-pr helper script was written by Erik Martin-Dorel and it is
  distributed under the MIT license <//opensource.org/licenses/MIT>.
```

### Installation

To be able to use `git pr` in a (Bash) terminal, you
just need to download the script
[git-pr](https://github.com/erikmd/git-scripts/raw/master/bin/git-pr),
set its execute permission, and put it in your `PATH`.

## [git-prw](bin/git-prw)

```
Facility to fetch a read/write branch from a GitHub repo Pull Request.

Usage:
  git prw <ID> [<REMOTE>] [-f]

Example:
  git prw 390 upstream

Summary:
  If the REMOTE argument is omitted, it defaults to "origin".
  REMOTE must point to a GitHub repository.

  This command checkouts the branch named "pr/ID" (if it doesn't exist
  yet, it fetches the source branch for the PR #ID in the REMOTE repo)
  and sets its upstream branch so that one can force-push to the fork
  (using an SSH URL); it reuses (if applicable) an existing remote
  matching that URL, or creates a remote named REMOTE-fork-for-pr-ID.

  Flag -f overwrites the local branch pr/ID even if it already exists.
  In general, it is a good idea to pass flag -f, unless we already ran
  "git pr ID REMOTE" and did commits in the local branch pr/ID.

  It requires curl <https://curl.se/> and (optionally) jq.

See also:
  - https://stackoverflow.com/a/62432946/9164010
  - https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/checking-out-pull-requests-locally
  - https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/allowing-changes-to-a-pull-request-branch-created-from-a-fork

Credits:
  The git-prw helper script was written by Erik Martin-Dorel and it is
  distributed under the MIT license <//opensource.org/licenses/MIT>.
```

### Installation

To be able to use `git prw` in a (Bash) terminal, you
just need to download the script
[git-prw](https://github.com/erikmd/git-scripts/raw/master/bin/git-prw),
set its execute permission, and put it in your `PATH`.
