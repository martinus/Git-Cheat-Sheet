# Git Cheat Sheet
## Concepts
* `master` Name of the default branch, similar to SVN's trunk.

Sources: [centralized workflow]

## Store credentials for https:// 

```bash
# cache credentials for a day
git config --global credential.helper "cache --timeout=86400"
# wincred for Windows, gnome-keyring for Linux, osxkeychain for Mac
git config --global credential.helper wincred
```

Sources: [stackoverflow], [git-credential-store]

##Workflows
### Simple Centralized Workflow
Everybody commits to `master` branch.

1. Clone a repository

   ```bash
   # automatically adds shortcut 'origin' back to parent repository
   git clone https://github.com/bitcoin/bitcoin.git
   ```

1. Make local changes

   ```bash
   git status
   git add <some files>
   git commit
   ```

1. Incorporate upstream changes

   ```bash
   # like SVN update: fetches changes and merges them.
   # --rebase: move all local commits to tip of master.
   #  Not strictly necessary, but removes superfluous “merge commit”
   git pull --rebase origin master
   ```

1. Push local `master` to central repository

   ```bash
   git push origin master
   ```

1. Resolve merge conflicts. Repeat until all conflicts resolved.

   ```bash
   # see where the problems are
   git status
   # Now edit files to your liking.
   git add <some files>
   git rebase --continue
   ```
Something bad happens? Go right back to before the pull with `git rebase --abort`

1. Publish features

   ```bash
   git push origin master
   ```

Sources: [centralized workflow]

### Feature Branch Workflow
TODO

Sources: [feature branch workflow]

---
* [stackoverflow]: http://stackoverflow.com/a/5343146/48181
* [git-credential-store]: https://git-scm.com/docs/git-credential-store
* [centralized workflow]: https://www.atlassian.com/git/tutorials/comparing-workflows/centralized-workflow
* [feature branch workflow]: https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow