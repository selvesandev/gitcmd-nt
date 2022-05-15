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

> stashing `git stash`
To save my changes before actually making a commit. Remove all the changes that has been done but saving it which is recoverable.

```terminal
git stash // remove or undo all the changes and save it for future
```

```terminal
git stash pop // recover all the changes that had been stashed

// or 

git stash apply

```

Difference between pop and apply.

1) Pop will recover all the stashed changed and remove it from the stash.
2) Apply will recover all the stashed changed by will not remove it from the stash and can be applied in multiple places.

> You can keep doing stash in order to add multiple stashed changes. The order is according to the stashed order.

```terminal
git stash list // to view all the stashed.
```

If you do `git stash pop` only the lates stash is going to be popped.

To reference particular stashed changes you can used the stashed id.

```terminal
git stash apply stash@{2}
```

If you aren't using pop. You can manually remove stash.

```terminal
git stash drop@{1}
```

```terminal
git stash clear // will remove all the stash.
```
