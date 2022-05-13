# GIT Commands

> Setup default editor as `vscode` on `git commit`.

```terminal
git config --global core.editor "code --wait"
```

For this to work your vscode path as to be setup as `code` in the terminal.

> View only a line of git commmit

```terminal
git log --oneline
```

> HEAD (Branch Reference)

A pointer that referes to a current location in a repository. It points to a particular branch location.

> Difference between `git switch` and `git checkout`.

`git switch` is new and `git checkout` is old school.

```terminal
git switch -c <branch-name> // create a new branch and switch to it.
```

```terminal
git checkout -b <branch-name> // create a new branch and switch to it.
```

> git diff
