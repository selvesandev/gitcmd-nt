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

## HEAD

> HEAD (Branch Reference)

A pointer that referes to a current location in a repository. It points to a particular branch location.

## GIT SWITCH

> Difference between `git switch` and `git checkout`.

`git switch` is new and `git checkout` is old school.

```terminal
git switch -c <branch-name> // create a new branch and switch to it.
```

```terminal
git checkout -b <branch-name> // create a new branch and switch to it.
```

**NOTE** `git switch` will also change the branch and if the branch is not in your local repository but in remote repository it is going to detech it and fetch if from the remote repository and switch to it.

## GIT DIFF

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
git diff commit_hash..ano_commit_hash
```

## STASHING

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

## GIT CHECKOUT TO COMMIT

> Cheking out to a commit.

You are in a `detached HEAD` state. Head usually refers to a branch not to a specific commit.

> Checking out to a commit with HEAD reference.

1) HEAD~1 referes to the commit before HEAD (parent).
2) HEAD~2 referes to the 2 commit before HEAD (grandparent).
3) or HEAD~8 (HEAD~N)

```terminal
git checkout HEAD~1
```

Note: Again `git checkout HEAD~1` would when you are aready at `git checkout HEAD~1` then this would move your head to again to -1.  
If you keep doing `git checkout HEAD~1` then you would be going back to your commit where your current HEAD is -1 i.e previous commit.

**`git checkout -` this would move you to the branch that you where right before current HEAD.**.

example.

```terminal
//if you are currently at master.

git checkout -b new-branch // will move you to new-branch

git checkout - // will move you back to master. because you were previously at master.
```

## DISCARDING CHANGES WITH CHECKOUT

> Discarding Changes `git checkout HEAD <file>` You can use the shorter version `git checkout -- <file or files>`.

To remove all the uncommited changes from a file or reset all the changes from a file to make it look like your last commit.

## GIT RESTORE

`git restore <file>` also does the same (restore all the changes back to where it was).

1) `git restore file.txt` is same as `git checkout HEAD file.txt`
2) `git restore --source HEAD~2 app.js`. will change the file to 2 commit prior to HEAD for only `app.js`.
3) `git restore app.js` will again change the file to the HEAD i.e the most recent commit.

## GIT RESET

> `git reset <commit_hash>` This will remove all the commits that after the mentioned hash but will not remove the changes. The changes will still be present in the files. i.e we do not loose the changes we only loose the commits.

...

> `git reset --hard <commit_hash>` This will remove all the commits that after the mentioned has and will also remove all the changes.

## GIT REVERT

> `git revert <commit-hash>`. Both revert and reset will undo changes from a commit. But the way they accomplish it is different. Reset removes commit entirely and moves the branch pointer backwards as if the commit never occured. Revert will do something different it will create a new commit and in that new commit it undoes the changes from an earlier commit instead of just deleting everything.

## Remote Branch

```terminal
git branch -r // checkout all the remote branches
```

```terminal
git switch branch-name // check if the remote has this branch create this branch locally and checkout to this branch and link this branch with remote.
```

## FETCH VS PULL

### FETCH

Fetching allows us to download changes from a remote repo to local(remote-tracking) repository but those changes will not be integrated to our local files (current HEAD). It lets you see what others have been working on, without having to merge those changes. Safe to do anytime.

```terminal
git fetch origin // will fetch all the remote changes but will not change our files.

git status // to see the message -> Your branch is behind 'origin/master' by 1 commit

git checkout origin/master // to check what are the changes (detached from HEAD)
```

Remote branch are not automatically listed with `git branch -r`

1) Create a new branch in your remote repository from github.
2) `git branch -r` this will not list your remote branch because it is not present in your local repository.
3) `git fetch` will fetch the remote repository but will not show up in the files system.
4) `git branch -r` will not show the remote branch.

### PULL

GIT PULL = **git fetch + git merge**

Git pull is another command to retrieve from remote repository. Unlike fetch, pull actually updates our HEAD branch with whatever changes are retrived. `go and download data from github repo and immediately update my local repository`

The branch that you are in right now is going to be updated when you pull from any other remote branch. Git pull might have also have some merge conflicts.

Shorter pull syntax.

`git pull`

This will fetch from the remote origin from the branch that you are on locally.

### GIST

A simple way to share code snippist. Not sharing a whole repository.

<https://gist.github.com/>

### Github Pages

You can get project sites and user sites. Only 1 user sites is available (selvesandev.github.io). Unlimited project sites can be hosted. (selvesandev.github.io/repo-name).

Go to repository `Setting` > `Github Pages`

### Collaborate on Open Source Project

1) Fork the original repository.
2) Clone your forked repository.
3) Also add a remove origin to the main original project so that you can pull from it `git remote add upstream <your_main_project_repo_origin_url>`.
4) Make you changes and pushed to your forked repository.
5) Now that your forked repository is ahead from the original repository.
6) Create a pull request to original repository.

**To pull from upstream** repository

```terminal
git pull upstream main //main is the branch name.
```

### Rebasing
