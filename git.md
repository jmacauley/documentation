# Git commands
Here are git commands I use most often on github and gitlab captured in one locations so I don't need to google endlessly.  Also, [Oh Shit, Git!?!](https://ohshitgit.com/) is a good resouce to help recover from stupid mistakes.

## Clone a branch locally

```
git clone <url>                 # clone a repo locally using the URL.
```

## List commits on branch

```
git log
```

## Create a branch

```
git checkout -b ＜new-branch＞                     # create a new branch from master.
git checkout -b ＜new-branch＞ ＜existing-branch＞ # create a new branch from an existing branch.
git checkout ＜existing-branch＞                   # switch to an existing branch.
git switch <existing-branch>                       # switch to an existing branch.
git branch                                         # list all branches in the current repo.
git remote -v                                      # show remote repositories and their name.
```

## Commit changes to branch

```
git status                      # view files changed locally.
git add *                       # add all locally changed files to the update.
git commit -m "update reason."  # commit the locally changed files.
git push                        # push the local commit to repo.
```

## Merge commits from main onto branch

```
git checkout oscars             # gets you "on branch oscars"
git fetch origin                # retrieve the latest meta-data info from the origin.
git merge origin/master         # merge commits from master branch onto current branch.
```

Update your local working branch with commits from the remote, but rewrite history so any local commits occur after all new commits coming from the remote, avoiding a merge commit.

```
git pull --rebase
```

## Revert commits from branch
Here we will make the current branch point to the older commit we would like to uses as the reference for our reversion.  This is rewriting the history of the branch, so commits performed after f414f31 will no longer be included in the history of the master branch.

```
git reset –hard f414f31
```

The previous command is considered a nuclear option as it removes the commits that have occured after the commit specified in the reset.  If you want to maintain the commit history, but set the contents of the branch to the commit specified in the reset, then use the following command:

```
git reset –hard f414f31
git reset –soft HEAD@{1}
git commit -m “Reverting to the state of the project at f414f31”
```