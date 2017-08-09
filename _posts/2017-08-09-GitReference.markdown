---
layout:     post
title:      "Git Reference"
subtitle:   "Full sheet of useful git commands"
date:       2017-08-09
author:     "Rob"
---

# Setup

```  
git clone url 
```
> Clone a repository specified by url. This is similar to “checkout” in some other version control systems such as Subversion and CVS.

``` 
git init
```
> Create an new git repository in the current directory or reinitialize an existing one.

```
git init --bare
```

> Create an new git repository in the current directory without an associated working tree. This is useful for repositories that serve as mirrors.

```
git update-server-info
```

> Allow a git repository to act as a dumb server (for remote access).

# Adding/Deleting

```
git add file1 file2 ...
```

> Add file1, file2, etc. to the project..

```
git add dir
```
> Add all files under directory dir to the project, including subdirectories.

```
git add .
```

> Add all files under the current directory to the project, including subdirectories.

```
git rm file1 file2 ...
```

> Remove file1, file2, etc. from the project (and the filesystem).

# Commiting

``` 
git commit file1 file2 ... [-m msg] 
```

> Commit changes in file1, file2, etc., optionally using commit message msg or otherwise opening editor for commit message entry.

```
git commit -a [-m msg]
```

> Commit changes made to all tracked files since the last commit, optionally using commit message msg or otherwise opening editor for commit message entry.

```
git commit --amend file1 file2 ... [-m msg]
```

> Re-commit previous commit, including file1, file2, etc., using previous commit message or, optionally, a new one given by msg.

# Sharing

``` 
git push [remote]
```

> Update the remote repository named remote with commits across all branches that are common between your local repository and remote. If remote is not specified, but a remote named “origin” is defined, then remote defaults to “origin”. Local branches that were never pushed to the server in the first place are not shared.

```
git push remote branch
```

> Update the remote repository named remote (e.g. “origin”) with commits made to branch since the last push. This is always required for new local branches (including “master” in a new repository). After the first explicit push, “git push” by itself is sufficient.

```
git pull remote
```

> Update the current branch with changes from the remote named remote (defaults to “origin” if not given). Note that for this to work, “.git/config” must define merge configuration variables for the current branch.

# Information

#### Changes and Differences

```
git status
```

> Show files added to the index, files with changes, and untracked files.

```
git diff
```

> Show unstaged changes made since your last commit.

```
git diff --cached
```

> Show changes staged for commit (i.e., difference between index and last commit).

```
git diff HEAD
```

> Show changes (staged and unstaged) in working directory since last commit.

```
git diff rev [path(s)]
```

> Show differences between working directory and revision rev, optionally limiting comparison to files found in one or more space-separated file paths or subdirectories given by path(s).

```
git diff rev1..rev2 [path(s)]
```

> Show differences between two revisions, rev1 and rev2, optionally limiting comparison to files found in one or more space-separated file paths or subdirectories given by path(s).

```
git diff rev1...rev2 [path(s)]
```

> Show differences between the last common ancestor of two revisions, rev1 and rev2, optionally limiting comparison to files found in one or more space-separated file paths or subdirectories given by path(s).


# File and Directory Contents

```
git show rev:file
```

> Show contents of file (specified relative to the project root) from revision rev.

```
git ls-files [-t]
```

> Show all tracked files (“-t” shows file status).

```
git ls-files --others
```

> Show all untracked files.


# Commit History

```
git log
```
Show recent commits, most recent on top.

```
git log [path(s)]
```

Show recent commits, most recent on top, limited to the file or files found on path(s) if given.

```
git log -p
```

Show recent commits, most recent on top, with full diffs.

```
git log -p [path(s)]
```

Show recent commits, most recent on top, with full diffs, limited to files found in one or more space-separated file paths or subdirectories given by path(s).

```
git log -g
```

Show recent commits, most recent on top, walking the full reflog entries instead of the commit ancestry chain up to the current HEAD. By default, “git log” reports all commits only up to the current HEAD, even if HEAD has descendents on the current branch (as, for example, might happen if you ran “git reset rev” to move HEAD to a previous point in history). The “-g” option will report the full history.

```
git log --stat [path(s)]
```

Show recent commits, with stats (files changed, insertions, and deletions), optionally limited to files found in one or more space-separated file paths or subdirectories given by path(s).

```
git log --author=author
```

Show recent commits, only by author.

```
git log --after="MMM DD YYYY"
```

Show commits that occur after a certain date, e.g. “Jun 20 2008”.

```
git log --before="MMM DD YYYY"

```

Show commits that occur before a certain date.

```
git whatchanged file
```

Show only the commits which affected file listing the most recent first.

```
git blame file
```

Show who authored each line in file.

```
git blame file rev
```

Show who authored each line in file as of rev (allows blame to go back in time).

```
git rev-list --all
```

List all commits.

```
git rev-list rev1..rev2
```
List all commits between rev1 and rev2.

```
git show rev
```

Show the changeset (diff) of a commit specified by rev.

```
git show rev -- path(s)
```

Show the changeset (diff) of a commit rev , optionally limited to files found in one or more space-separated file paths or subdirectories given by path(s).

# Searching

#### Searching for Content

```
git grep regexp
```

Search working tree for text matching regular expression regexp.

```
git grep -e regexp1 [--or] -e regexp2
```

Search working tree for lines of text matching regular expression regexp1 or regexp2.

```
git grep -e regexp1 --and -e regexp2
```

Search working tree for lines of text matching regular expression regexp1 and regexp2, reporting file paths only.

```
git grep -l --all-match -e regexp1 -e regexp2
```

Search working tree for files that have lines of text matching regular expression regexp1 and lines of text matching regular expression regexp2.

```
git grep regexp $(git rev-list --all)
```

Search all revisions for text matching regular expression regexp.

```
git grep regexp $(git rev-list rev1..rev2)
```

Search all revisions between rev1 and rev2 for text matching regular expression regexp.


# Searching Logs and Commit History

```
git log --grep regexp
```

Search commit logs for lines of text matching regular expression regexp.

```
git log --grep regexp1 --grep regexp2
```

Search commit logs for lines of text matching regular expression regexp1 or regexp2.

```
git log --grep regexp1 --and --grep regexp2
```

Search commit logs for lines of text matching regular expression regexp1 and regexp2.

# Branching

#### Listing Branches

```
git branch
```

List all local branches.

```
git branch -r
```

List all local and remote branches.


# Creating Branches

```
git branch new-branch
```

Create a new branch named new-branch, based on current branch.

```
git branch new-branch rev
```

Create a new branch named new-branch, based on revision specified by tree-ish rev.

```
git branch --track new-branch remote/remote-branch
```
Create a new tracking branch named new-branch, referencing, and pushing/pulling from, the branch named remote-branch on remote repository named remote.


# Checking Out Branches/Revisions

```
git checkout branch
```

Switch to branch named branch. This updates the working tree to reflect the state of the branch named branch, and sets HEAD to “.git/refs/heads/branch”.

```
git checkout rev
```

Switch to revision specified by tree-ish rev, without explicitly branching. Running “git checkout -b new-branch” will create a branch from the checked out version.


# Simultaneous Creating and Switching Branches

```
git checkout -b new-branch
```

Create a new branch named new-branch, referencing the current branch, and check it out.

```
git checkout -b new-branch rev
```

Create a new branch named new-branch based on the tree-ish rev, update the working tree to reflect its state, and check it out (switch to it).


# Deleting Branches

```
git branch -d branch
```

Delete the local branch named branch (fails if branch is not reachable from the current branch).

```
git branch -D branch
```

Force delete of the local branch named branch (works even if branch is not reachable from the current branch).

```
git branch -d -r remote/branch
```

Delete a “local remote” branch, i.e. a local tracking branch.

```
git push remote :heads/branch
```

Delete a branch named branch from a remote repository.

# Merging

In all of the following, a merge strategy can be specified by the “-s strategy” argument, which can be one of: “resolve”, “recursive”, “octopus”, “ours”, or “subtree”. If you tried a merge which resulted in a complex conflicts and would want to start over, you can recover with “git reset –hard”. If you accidently merged and want to unmerge, you can “git reset –hard ORIG_HEAD”.

```
git merge branch
```

Merge branch branch into the current branch and commit the result. This command is idempotent and can be run as many times as needed to keep the current branch up-to-date with changes in branch.

```
git merge branch --no-commit
```

Merge branch branch into the current branch, but do not autocommit the result. Allows for inspection or tweaking of the merge result before committing.

```
git merge branch --squash --commit
```

> Merge branch branch into the current branch as a single commit.

# Undoing

> Reverting is different from resetting in that reverts usually create new history while resets usually remove existing history. The changes of a revert are applied to the current state of the repository, and, if committed, results in a new repository state descending from the current one. Reverts are safe to publish even if they revert a previously published commit, and, in fact, are the correct way of dealing with the undoing of published commits. Resetting, on the other hand, represents (a possibly selective) “rewind” to a previous state in the history “starting again” from there. Resets should never be committed if they undo commits that have been published or pushed to remote repositories, as this would result in invalid object histories and commit ID’s in the remote repositories.

# Reverting

```
git revert rev
```

Revert the changes introduced by rev, and record a new commit that records it. This does not do the same thing as similarly named commands in other VCS’s such as “svn revert” or “bzr revert”.

```
git checkout path(s)
```

Re-checkout file or files specified by path(s), overwriting any local changes. This is most similar to “svn revert”.

```
git checkout -- path(s)
```

As above, but use this syntax if you have a branch or tag with the same name as a path given in path(s).

```
git checkout rev path(s)
```

Re-checkout file or files specified by path(s) to version specified by rev (which may be specified using a SHA1 commit ID, branch name, or tag), overwriting any local changes.

```
git checkout -f
```

Throw away all local changes since last commit, restoring working tree to last committed state (plus untracked files) and clearing index. Unlike “git reset –hard”, does not move HEAD, and so will not, for example, cleanly forget about a failed merged: use “git reset –hard” for this.

# Resetting

```
git reset
```

Resets the index (i.e., removes all changes staged for commit) but does not modify the working tree (i.e., the changes in the files are preserved), and does not change HEAD.

```
git reset rev -- path(s)
```

Restores file or files specified by path(s) to revision specified by rev, without changing HEAD.

```
git reset rev
```

Sets the current HEAD to the commit specified by rev (which may be specified using a SHA1 commit ID, branch name, or tag), and resets the index but not the working tree (i.e current changes in the working tree are preserved).

```
git reset --soft rev
```

Sets the current HEAD to the commit specified by rev, and does not modify the working tree, but keeps changes in the index for editing. For example, if something was forgotten or omitted in the previous commit, “git reset –soft HEAD^” will undo the last commit, and keep all changes in the index for editing and the next commit.

```
git reset --hard
```

Throw away all local changes since last commit, restoring working tree to last committed state (plus untracked files) and resetting both index and HEAD.

```
git reset --hard rev
```

Sets the current HEAD to the commit specified by rev, and changes the working tree to mirror the new HEAD (plus untracked files). For example, “git reset –hard ORIG_HEAD” will undo the most recent successful merge and any changes that occurred after. Useful for forgetting about the merge just done. If there are conflicts (the merge was not successful), use “git reset –hard” instead.

# Stashing

> Use “git stash” when you want to record the current state of the working directory and the index, but want to go back to a clean working directory. The command saves your local modifications away and reverts the working directory to match the HEAD commit.

```
git stash save [msg]
```

Save your local modifications to a new stash, and run “git reset –hard” to revert them. This is the default action when no subcommand is given. If msg is not explicitly given, then it defaults to “WIP on branch” where “branch” is the current branch name.

```
git stash list
```

List all current stashes.

```
git stash apply [stash]
```

Restore the changes recorded in the stash on top of the current working tree state. When no stash is given, applies the latest one (stash@{0}). The working directory must match the index.

```
git stash pop [stash]
```

Remove a single stashed state from the stash list and apply on top of the current working tree state. When no stash is given, the latest one (stash@{0}) is assumed.

```
git stash clear
```

Remove all the stashed states.

```
git stash drop [stash]
```

Remove a single stashed state from the stash list. When no stash is given, it removes the latest one. i.e. stash@{0}.

```
git stash branch new-branch [stash]
```

Creates and checks out a new branch named new-branch starting from the commit at which the stash was originally created, applies the changes recorded in stash to the new working tree and index, then drops the stash if that completes successfully. When no stash is given, applies the latest one.


# Cleaning

```
git clean -f
```

Remove all untracked files from working copy.

```
git clean -fd
```

Remove all untracked files and directories from working copy.

```
git clean -fX
```

Remove all ignored files from working copy.

```
git clean -fXd
```

Remove all ignored files and directories from working copy.

```
git clean -fx
```

Remove all untracked and ignored files from working copy.

```
git clean -fxd
```

Remove all untracked and ignored files and directories from working copy.

# Remotes

```
git remote add remote url
```

Adds a remote named remote for the repository at url.

```
git rm remote url
```
Remove reference to remote repository named remote: all tracking branches and configuration settings for remote are removed.

```
git push remote :heads/branch
```

Delete the branch branch from the remote repository named remote.

```
git remote prune remote
```

Prune deleted remote branches from git branch listing. These branches have already been removed from the remote repository named remote, but are still locally available in “remotes/remote”.

# Plumbing

```
test sha1-A = $(git merge-base sha1-B)
```

Determine if merging sha1-B into sha1-A is achievable as a fast forward; non-zero exit status is false.


# Configuration

You can add “--global” after “git config” to any of these commands to make it apply to all git repositories (writes to ~/.gitconfig).

```
git config user.email author@email.com
```

Set email for commit messages.

```
git config user.name 'author name'
```

Set name for commit messages.

```
git config branch.autosetupmerge true
```

Tells git-branch and git-checkout to setup new branches so that git-pull(1) will appropriately merge from that remote branch. Recommended. Without this, you will have to add “--track” to your branch command or manually merge remote tracking branches with “fetch” and then “merge“.


# Environment Variables

```
GIT_AUTHOR_NAME, GIT_COMMITTER_NAME
```

Full name to be recorded in any newly created commits. Overrides user.name in .git/config.

```
GIT_AUTHOR_EMAIL, GIT_COMMITTER_EMAIL
```

Email address to be recorded in any newly created commits. Overrides user.email in .git/config.