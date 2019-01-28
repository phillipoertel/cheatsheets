# TOC

<!-- MarkdownTOC autolink="true" levels="1" -->

- [BRANCHES](#branches)
- [MERGING](#merging)
- [COMMITING](#commiting)
- [SHOW STUFF](#show-stuff)
- [PUSH](#push)
- [TAG](#tag)
- [REVERT](#revert)
- [REMOTE](#remote)
- [RESOURCES](#resources)

<!-- /MarkdownTOC -->

# BRANCHES

## move commits from one branch to another

```
git branch newbranch # on master
git reset --hard HEAD~3 # Go back 3 commits. You *will* lose uncommitted work.
git checkout newbranch
```

## prune (purge) git remote branches

```
git remote prune origin
```

## pull & merge remote branch directly into local

```
git pull origin remote-branch
```

## make a branch at an earlier revision

```
git branch branchname {sha1-of-commit or HEAD~3}
```

## check out and track remote branch

```
git co -t {git-remote}/{branch-name}
```

## check out previous branch

```
git co -
```

## find out which branches contain a given commit

```
git branch -r --contains 4993b33d
```

# MERGING

## prevent merge commits when pulling

```
git merge --rebase ...
-> aliased to 'git pr'
```

## in a merge conflict file, overwrite my local changes with the remote version:

```
git checkout --theirs config/locales/en.yml
git checkout --ours /path/to/file # alternatively
```

## check if one branch has been merged into another
```
git br --merged master
```

# COMMITING

## append to a previous commit

```
git rebase -i HEAD^^ # ^as many as you want to go back
```

## make an empty commit

```
git commit --allow-empty -m "empty commit"
```

# SHOW STUFF

## show changes in some files between revisions

```
git diff --name-only 13b315b..HEAD | grep scss | xargs git diff 13b315b..HEAD $1
```

## show file at a certain revision

```
git show HEAD~4:index.html
```

## search commit history / logs

```
git log --grep=rave
```

## show commits of author and time range

```
git log --after="2019-01-22 23:59:59" --before="2019-01-24 00:00" --author Phillip
```

# PUSH

## push local branch to different remote branch

```
git push origin local-name:remote-name
```

# TAG

## push a tag

```
git push origin tagname # analog branches
```

# REVERT

## revert committed changes without loosing them

```
git reset HEAD~1 --soft
```

# REMOTE

## Rename a repository

```
git remote set-url origin new_url
```

# RESOURCES

http://mindspill.net/computing/linux-notes/git-notes/
https://www.toptal.com/git/tips-and-practices
http://ohshitgit.com/

