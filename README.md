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

> git diff HEAD

changes that we've made since last HEAD. `git diff` will not shown the difference once the file has been added (`git add .`) since it is the unstaged changes wherease git diff HEAD will show the difference of all staged and unstagged changes.

```terminal
git diff (--staged or --cached) // will show difference of only stagged changes.
```

```terminal
git diff --stagged file_name // to view of single file.
```

> Difference comparison between two branches.

```terminal
git diff master..another_branch
```

> companring changes in commits

```terminal
git diff commit_hash..ano_commit_hash //
```
