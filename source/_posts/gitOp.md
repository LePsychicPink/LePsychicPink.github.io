---
title: Git operation
date: 2024-09-04 00:00:34
tags: git
categories: programming
cover: img/hisameTop.png
---

### Branch

| Operation                    | command                           |
| ---------------------------- | --------------------------------- |
| create new branch            | `git branch {branch name}`        |
| check branch                 | `git branch`                      |
| switch branch                | `git switch {branch name}`        |
| delete branch                | `git branch -d {branch name}`     |
| switch and create new branch | `git switch -c {new branch name}` |

### Commit

| Operation                  | command                                         |
| -------------------------- | ----------------------------------------------- |
| Commit single file         | `git commit {path_to_file} -m "commit message"` |
| commit all                 | `git commit -a -m "message`                     |
| amend commit               | `git commit -m "message" --amend`               |
| Go back to specific commit | `git reset {commitID}`                          |

Staging → `git add {files}`

Unstaging → `git restore --staged {files}`

Cancel git reset 

Stashing untracked file → `git stash --include-untracked`

### Reset
```
git reset 'HEAD@{1}'
```
or
```
git reset {commitID}
```
reset the base to certain commit and keep your own working directory

```
git reset --hard {commitID}
```
force the working directory into the certain commit, changes will not be kept
### Remove a commit / force push old commit

```
git reset --hard {commitID}
git push --force
```

### When you hard reset and lost all your changes
1. Find the lost commit id by
```
git reflog
```
2. hard reset to the commit
```
git reset --hard {lostCommitID}
```