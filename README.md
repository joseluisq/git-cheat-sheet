# Git cheat sheet

> Another Git cheat sheet yet :octocat:

## Menu
- [Configuration](#commiting)
- [Commiting](#commiting)
- [Branching](#branching)
- [Pulling](#pulling)
- [Pushing](#pushing)
- [Logging](#logging)
- [Tagging](#tagging)
- [Reflog](#reflog)
- [Resolve conflicts](#resolve-conflicts)
- [Aliases](#aliases)
- [Bonus](#bonus)
- [Resources](#resources)

## Configuration

#### User setup

```sh
git config user.name "Name"
git config user.email '<name@email.com>'
```

_**Tip**: Add --global flag for global config._

#### Sign commits using a GPG key

List your gpg keys:

```sh
gpg --list-secret-keys --keyid-format LONG
/Users/username/.gnupg/secring.gpg
  ------------------------------------
sec   4096R/2AA5B24170567CE0 2019-01-01 [expires: 2020-01-01]
```

__Tip:__ For a GPG key setup check out [Generating a new GPG key](https://help.github.com/en/articles/generating-a-new-gpg-key)

Add your GPG signing key in Git globally:

```sh
git config --global user.signingkey 2AA5B24170567CE0
```

__Tip:__ For disable signing commits temporarily try: `git config --global commit.gpgsign false`

#### Global .gitignore file

```sh
git config --global core.excludesfile ~/.gitignore
```

#### Add remote origin

```sh
git remote add <remote_origin> <repo_url>
```

#### Remove remote origin

```sh
git remote remove <remote_origin>
```

## Commiting

#### Show the working tree status

```sh
git status
```

_**Tip**: Use `-sb` flag to see the status in a compact way._

#### Stage files to commit

```sh
git add <some_files_or_directories>
```

_**Tips**: Use a dot `git add .` to stage all files for commit._

#### Commit a change

```sh
git commit <some_files_or_directories>
```

_**Tips**: Add `-m "Message here"` to commit with a message directly._

#### Change last commit message

```sh
git commit --amend
```

_**Tip**: Add `--author="Name <name@email>"` to override author._

#### Revert previous commit but keeping last changes

```sh
git reset HEAD^
```

#### Revert previous commit (no safety)

_**Caution**: This command throws away all your uncommitted changes. For safety, you should always check that the output of `git status` is clean (that is, empty) before using it. [See this thread for more details](https://stackoverflow.com/a/9530204/2510591)._

```sh
git reset --hard HEAD
```

#### Cherry-pick a commit

[Cherry pick](https://git-scm.com/docs/git-cherry-pick) means to choose a commit from one branch and apply it onto another. [See this thread for more details](https://stackoverflow.com/a/9339460/2510591).

```sh
git cherry-pick <other_branch_parent_commit> -m 1
```

**Note**: Parent number starting from 1. [See this thread for more details](https://stackoverflow.com/a/9339460/2510591).

#### Cherry-pick last commit

```sh
git cherry-pick $(git rev-parse <other_branch_name>) -m 1
```

## Branching

#### Create a new branch and start it

```sh
git checkout -b <new_branch>
```

#### Checkout a remote branch

```sh
git checkout -tb <local_branch> origin/<remote_branch>
```

#### Rename a branch

```sh
git branch -m <new_branch_name>
```

_**Tip**: Use `-M` flag to forcing instead._

#### List all branches

```sh
git branch -a
```

#### List remote branches

```sh
git branch -r
```

#### Delete branches

```sh
git branch -d <branch_name_1> <branch_name_2> <branch_name_n>
```

_**Tip**: Tip: Use `-D` flag to forcing instead._

#### Merge two branches

```sh
git checkout <target_branch>
git merge <source_branch>
```

_**Tip**: Add `--squash` flat for a squash merging._

## Pulling

#### Pull changes from remote server but saving uncommitted changes

This command makes this for you:

- Save your uncommitted changes locally with `git stash`.
- Local changes you made will be rebased on top of the remote changes.
- Return your uncommitted changes locally again.

```sh
git pull <remote_origin> <target_branch> --rebase --autostash
```

_**Tip:** Skip `--rebase` if you want to merge your changes with the remote changes._

## Pushing

#### Push changes to remote server

```sh
git push <remote_origin> <branch_name>
```

## Logging

#### Show log info of last commit 

```sh
git log -1 HEAD
```

#### Show logs in a fancy way

```sh
git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

## Tagging

#### Create a tag

```sh
git tag v1.0.0
```

#### Delete a tag

```sh
git tag -d v1.0.0
```

## Reflog

#### Find and manage the history of all your Git stuff

```sh
git reflog
```

## Resolve conflicts

TODO

## Aliases

If you don't want to type the entire text of each of the Git commands above, you can easily set up an alias for each command and then just run it.

__Example:__ We will create an alias `last` that shows log info of the last commit.

```sh
git config --global alias.last 'log -1 HEAD'
```

Then just run:

```sh
git last
```

## Bonus

- [git-useful-aliases](https://github.com/joseluisq/git-useful-aliases) — Set of useful Git aliases.
- [GitNow](https://github.com/joseluisq/gitnow) — Speed up your Git workflow.

## Resources

- https://git-scm.com/docs
- https://github.com/nvie/gitflow
- https://github.com/jakubpawlowicz/git-cheat-sheet
- https://github.com/git-tips/tips
- https://github.com/razzius/git-tricks

## Contributions

Feel free to send some [Pull request](https://github.com/joseluisq/git-cheat-sheet/pulls) or [issue](https://github.com/joseluisq/git-cheat-sheet/issues).

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](http://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [Jose Quintana](https://git.io/joseluisq) has waived all copyright and related or neighboring rights to this work.
