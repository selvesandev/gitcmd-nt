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

Combining two branches can be done by `merging` or by `rebasing`.

When you merge a feature or fix branch to `master` or `master` to your feature or fix branch. You will get a extra commit (merge commit) on your commit log.

If there is large amount or number of the extra merge commit our history log is cluttered. It's muddied, uglier and hard to follow.

So to make clean commit history and to group together all the commits in a logical way you minimize the number of those commits with git `rebase`.

If you are on a feature or fix branch and run `git rebase master`. This will move all the commits in your feature or fix branch to the tip of your master branch's commit.

When you have merge conflict when doing rebase your rebase process will be half done (not complete). In that situation you can do two things. `abort` or `continue`.

```terminal
git rebase --abort // useful when conflict on rebase.
```

or if you fix your merge conflict you can.

```terminal
git rebase --continue
```

### Rebasing to rewrite history

Besides using rebasing as an alternative to commit we can also use for clean up toop. we can

1) edit commits.
2) change the contents of a commit.
3) we can drop or delete commit.
4) we can re order commits.

```terminal
git rebase -i HEAD~4
```

#### Combine two commits as one

```terminal
git rebase -i HEAD~4
```

This command will open the list of your commits and allow you to modify them with specific list of commands. The commands are

> `pick` don't change anything just keep it like it was before.

`edit`

> `drop` to drop a commit.

`squash`

> `reword` to update the commit message. you can reword multiple at the same time.

`edit`

> `fixup` take the content of a commit and add it to another(previous) commit. Mark fixup to the commit whose file you want to move.

**NOTE** all the subsequent commits after the rebase commit will change it's hash.

### Versioning

* 1.0.0 = Major release
* 1.0.1 = Patches / Fixes
* 1.1.0 = Minor Release
* 2.0.0 = Major Release that might not have backward compatibility and might have breaking changes.

### Tags

* List all tags

```terminal
git tag -l // list all


git tag -l "*beta" // filter all tags that contains beta text.
```

We are in a detached mode if we checkout to a `tag`. Because `tag` always points to a commit.

* Diff between two tags.

```terminal
git diff v17.0.0 v17.0.1
```

* Creating a tag.

```terminal
git tag <tag-name>
```

When a tag is created it will point to the commit wherever the HEAD is right now.

* Anotated Tags

will prompt you to an editor.

```terminal
git tag -a <tag-name>

// or 

git tag -m "message" <tag-name>

```

* View more information about a particular tag.

```terminal
git show <tag-name>
```

* Force a tag that already exists.

```terminal
git tag -f <tag_name>
```

* Delete a tag

```terminal
git tag -d <tag_name>
```

* Push tags

```terminal
git push <tag_name> //push single tags
```

```terminal
git push --tags //push all tags
```

### Local Config File

```terminal
git config --local user.name "your_user_name" //write user name

git config --local user.name // read user name

```

### Git Database

Git is a key value data store. We can store any kind of data in it and it will hand us back a key for that data The keys that we get back are `sha-1` checksums which we use to retrive the data back.

> Save value and get the encrypted key

```terminal
echo "hi" | git hash-object --stdin

git hash-object <filename> //whenever the content of this file is changed a new sha-1 key will be generated
```

to write the value inside .git folder

```terminal
echo "hi" | git hash-object --stdin -w
git hash-object <file_name> -w
```

> Retrive a value

```terminal
git cat-file -p <hash_code>

git cat-file -p <hash_code> -p // [-p(pretty) is optional ]

git cat-file -p <hash_code> > <file_name> // retrive and write to a file.
```

> Trees

Tree is a store mechanism tabled structure of git contents. Tree are a git object used to store the contents of a directory. Each tree contains pointer that can refer to blob and to other trees. Each entry in a tree contains the `SHA-1` hash of a blob or tree, as well as the mode, type and file name.

```terminal
git cat-file -p master^{tree}
```

### Reflog

Reflog is a history of actions that was done in git.

```terminal
git reflog show HEAD
```

> Reflog references (Time references)

All the logs in the reflog has a timestamp associated with it.

```terminal

git reflog master@{one.week.ago}

```

NOTE **Will not go back over 90 days and will only work on local changes**
