---
layout: post
category: "git"
title:  "Git experience"
tags: [git]
excerpt: "git"
---

# Branch

## Create
### Create new local branch

    git checkout -b "branch_name"

### Create remote branch from exist location branch

    git push orign “branch_name”

### Create local branch from exist remote branch

    git fetch
    git checkout “branch_name”
## List branch
#### List local branch

    git branch

#### List remote branch

    git branch -ar

#### List all branch

    git branch -a
    
## Switch branch

    git checkout “branch_name”

## Delete
### Delete a branch

    git branch -D “branch_name”

### Delete all local branch except
1)
```
git branch | grep -v "develop" | grep -v "master" | xargs git branch -D // delete all branch but keep develop and mater
```
2)
```
for b in `git branch --merged | grep -v \*`; do git branch -D $b; done // delete all branch except current branch
```

# File
### Checkout file (only work for tracked file)

    git checkout “file_name”

### Clean file (work for untracked file)

    git clean “file_name”

### Clean all file and folder

    git clean -f -d // to get rid of untracked files and directories

# Commit
### Rebase

    git rebase -i HEAD~2 // 2 là số commit muốn rebase

### Rename last commit

    git commit --amend
    git commit --amend -m "New commit message"

## Rename Branch

    git branch -m <newname>

## Store password
>Password will stored forever

Step 1) `git config credential.helper store`  
Step 2) Use `git pull` or `git push ...`  
Step 3) Enter username and password  
Step 4) Username and password is already stored   

**Note**  
To update, redo step from 1 -> 4  

**Reference**  
https://stackoverflow.com/a/35942890/5381331
### Cache password
> Password will store till it's timeout. However, it will reset after we reset computer

https://help.github.com/articles/caching-your-github-password-in-git/
### **Check out remote branch**

    git fetch
    git checkout branch_test

## My alias
```
alias gs='git status'
alias gb='git branch'
alias gc='git checkout'
alias gaa='git add --all'
alias gcam='git commit --amend'
alias gcm='git commit -m'
alias gpo='git push origin'
alias gpof='git push origin -f'
alias gpr='git pull --rebase'
```

